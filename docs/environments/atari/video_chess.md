---
title: VideoChess
---

# VideoChess

```{figure} ../../_static/videos/atari/video_chess.gif
:width: 120px
:name: VideoChess
```

This environment is part of the <a href='..'>Atari environments</a>. Please read that page first for general information.

|   |   |
|---|---|
| Action Space | Discrete(10) |
| Observation Shape | (210, 160, 3) |
| Observation High | 255 |
| Observation Low | 0  |
| Import | `gymnasium.make("ALE/VideoChess-v5")` |

For more VideoChess variants with different observation and action spaces, see the variants section.

## Description

VideoChess is missing description documentation. If you are interested in writing up a description, please create an issue or PR with the information on the Gymnasium github.

## Actions

VideoChess has the action space `Discrete(10)` with the table below lists the meaning of each action's meanings.
As VideoChess uses a reduced set of actions for `v0`, `v4` and `v5` versions of the environment.
To enable all 18 possible actions that can be performed on an Atari 2600, specify `full_action_space=True` during
initialization or by passing `full_action_space=True` to `gymnasium.make`.

| Value   | Meaning    | Value   | Meaning   | Value   | Meaning     |
|---------|------------|---------|-----------|---------|-------------|
| `0`     | `NOOP`     | `1`     | `FIRE`    | `2`     | `UP`        |
| `3`     | `RIGHT`    | `4`     | `LEFT`    | `5`     | `DOWN`      |
| `6`     | `UPRIGHT`  | `7`     | `UPLEFT`  | `8`     | `DOWNRIGHT` |
| `9`     | `DOWNLEFT` |         |           |         |             |

## Observations

Atari environment have two possible observation types, the observation space is listed below.
See variants section for the type of observation used by each environment id.

- `obs_type="rgb" -> observation_space=Box(0, 255, (210, 160, 3), np.uint8)`
- `obs_type="ram" -> observation_space=Box(0, 255, (128,), np.uint8)`

Additionally, `obs_type="grayscale"` cause the environment return a grayscale version of the rgb array for observations with the observation space being `Box(0, 255, (210, 160), np.uint8)`

## Variants

VideoChess has the following variants of the environment id which have the following differences in observation,
the number of frame-skips and the repeat action probability.

| Env-id                | obs_type=   | frameskip=   | repeat_action_probability=   |
|-----------------------|-------------|--------------|------------------------------|
| ALE/VideoChess-v5     | `"rgb"`     | `4`          | `0.25`                       |
| ALE/VideoChess-ram-v5 | `"ram"`     | `4`          | `0.25`                       |

## Difficulty and modes

It is possible to specify various flavors of the environment via the keyword arguments `difficulty` and `mode`.
A flavor is a combination of a game mode and a difficulty setting. The table below lists the possible difficulty and mode values
along with the default values.

| Available Modes   | Default Mode   | Available Difficulties   | Default Difficulty   |
|-------------------|----------------|--------------------------|----------------------|
| `[0, 1, 2, 3, 4]` | `0`            | `[0]`                    | `0`                  |

## Version History

A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the "ALE" namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release