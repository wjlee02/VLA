### 양팔 VLA 학습을 위한 Lerobot 데이터셋 만들기

#### 1. HDF5 -> Lerobot Dataset(v2.1)

##### episode_*.hdf5 예시
```text
├── observations/
│   ├── images/
│   │   ├── sensor_1        (T, H, W, 3) uint8
│   │   ├── sensor_2        (T, H, W, 3) uint8
│   │   └── sensor_3        (T, H, W, 3) uint8
│   └── qpos/
│       ├── robot_1         (T, 7) float32
│       └── robot_2         (T, 7) float32
└── qaction/
    ├── robot_1             (T, 7) float32
    └── robot_2             (T, 7) float32
```

##### 변환 명령어
```
python scripts/convert_from_hdf5.py \
  --data-path ??? \
  --out-dir ??? \
  --task "???" 
```



#### 2. Lerobot Dataset(v2.1) + norm stats 추가

##### 추가 명령어
```
python scripts/compute_norm_stats.py \
  --data-paths lerobot_dataset \
  --output-path lerobot_dataset/meta/norm_stats.json \
  --embodiment-id 0 \
  --delta-mask True True True True True True False True True True True True True False \
  --action-chunk 50 \
  --action-dim 14
```

##### Lerobot Dataset(v2.1) 예시
```
├── data
│   └── chunk-000
│       ├── episode_000000.parquet
│       ├── episode_000001.parquet
│       └── ....
├── meta
│   ├── episodes_stats.jsonl
│   ├── episodes.jsonl
│   ├── info.json
│   ├── stats.json
│   └── tasks.jsonl
└── videos
    └── chunk-000
        ├── observation.images.cam_high
        │   ├── episode_000000.mp4
        │   ├── episode_000001.mp4
        │   └── ....
        ├── observation.images.cam_left_wrist
        │   ├── episode_000000.mp4
        │   ├── episode_000001.mp4
        │   └── ....
        └── observation.images.cam_right_wrist
            ├── episode_000000.mp4
            ├── episode_000001.mp4
            └── ....
```



#### 3. Lerobot Dataset(v2.1) -> Lerobot Dataset(v3.0)

##### Lerobot Dataset(v3.0) 예시
```text
├── data
│   └── chunk-000
│       └── file-000.parquet
├── meta
│   ├── episodes
│   │   └── chunk-000
│   │       └── file-000.parquet
│   ├── info.json
│   ├── stats.json
│   └── tasks.parquet
└── videos
    ├── observation.images.cam_high
    │   └── chunk-000
    │       └── file-000.mp4
    ├── observation.images.cam_left_wrist
    │   └── chunk-000
    │       └── file-000.mp4
    └── observation.images.cam_right_wrist
        └── chunk-000
            └── file-000.mp4
```



#### 4. Lerobot Dataset(v3.0) + image stats 추가



#### 5. VLA 학습





##### 참고자료
- Lerobot      [Click here to try](https://github.com/huggingface/lerobot)
- Giga-Brain-0 [Click here to try](https://github.com/open-gigaai/giga-brain-0)

