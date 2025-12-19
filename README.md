## VLA 학습을 위한 Lerobot 데이터셋 만들기

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
  --data-path after \
  --out-dir ??? \
  --task "설명" 
```

#### 2. Lerobot Dataset(v2.1) + norm stats 추가

##### Lerobot Dataset(v2.1) 예시


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
