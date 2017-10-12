---
layout: phaser-game
title: "Star Collector"
date: 2017-10-12
tags: game 2d platform
---

You can check the source code [here](https://github.com/cesarlopezfab/star-collector).


<script type="text/javascript">
  var game = new Phaser.Game(800, 600, Phaser.AUTO, '{{ layout.container }}', {preload: preload, create: create, update: update});
  var platforms;
  var score = 0;
  var scoreText;
  var cursors;

  function preload() {
    game.load.image('sky', '{{ layout.assets }}/sky.png');
    game.load.image('ground', '{{ layout.assets }}/platform.png');
    game.load.image('star', '{{ layout.assets }}/star.png');
    game.load.spritesheet('dude', '{{ layout.assets }}/dude.png', 32, 48);
  }

  function createPlatforms() {
    platforms = game.add.group();
    platforms.enableBody = true;

    var ground = platforms.create(0, game.world.height - 64, 'ground');
    ground.scale.setTo(2, 2);
    ground.body.immovable = true;

    platforms.create(400, 400, 'ground').body.immovable = true;
    platforms.create(-150, 250, 'ground').body.immovable = true;
  }

  function createPlayer() {
    player = game.add.sprite(32, game.world.height - 150, 'dude');
    game.physics.arcade.enable(player);

    player.body.bounce.y = 0.2;
    player.body.gravity.y = 300;
    player.body.collideWorldBounds = true;

    player.animations.add('left', [0, 1, 2, 3], 10, true);
    player.animations.add('right', [5, 6, 7, 8], 10, true);
  }

  function createStars() {
    stars = game.add.group();
    stars.enableBody = true;

    var numberOfStars = 12;
    var starGravity = 6;
    var starBaseBounce = 0.7;

    for (var i = 0; i < numberOfStars; i++) {
      var star = stars.create(i * 70, 0, 'star');
      star.body.gravity.y = starGravity;
      star.body.bounce.y = starBaseBounce + Math.random() * 0.2;
    }
  }

  function create() {
    game.physics.startSystem(Phaser.Physics.ARCADE);
    game.add.sprite(0, 0, 'sky');

    createPlatforms();
    createPlayer();
    createStars();

    scoreText = game.add.text(16, 16, 'Score: 0', { fontSize: '32px', fill: '#000' });
    cursors = game.input.keyboard.createCursorKeys();
  }

  function handlePlayerMovement(hitPlatform) {
    player.body.velocity.x = 0;

    if (cursors.left.isDown) {
      player.body.velocity.x = -150;
      player.animations.play('left');
    } else if (cursors.right.isDown) {
      player.body.velocity.x = 150;
      player.animations.play('right');
    } else {
      player.animations.stop();
      player.frame = 4;
    }
    var ableToJump = cursors.up.isDown && player.body.touching.down && hitPlatform;
    if (ableToJump) {
      player.body.velocity.y = -350;
    }
  }

  function update() {
    var hitPlatform = game.physics.arcade.collide(player, platforms);
    game.physics.arcade.collide(stars, platforms);
    game.physics.arcade.overlap(player, stars, collectStar, null, this);

    handlePlayerMovement(hitPlatform);
  }

  function collectStar (player, star) {
    star.kill();
    score += 10;
    scoreText.text = 'Score: ' + score;
  }

</script>
