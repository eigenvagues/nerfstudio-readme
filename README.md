# nerfstudio

> [!NOTE]
> Documentation and troubleshooting notes for nerfstudio.\
> Windows 11 IoT LTSC 2024.\
> Dec 2025.

Find the install guide [here](install.md)

---

> [!IMPORTANT]
> Run all commands with **elevated** VS22's native cmd (x64 Native Tools Command Prompt for VS 2022 LTSC 17.8).\
> `Ctrl + C` to exit any job.

### Training
```
ns-train [method] --data [data-path]
```

### Checkpoints
```
ns-train [method] --data [data-path] --load-dir {outputs/[dataset-name]/[method]/[date]/nerfstudio_models}
```

### Viz
```
ns-viewer --load-config {outputs/[dataset-name]/[method]/[date]/config.yml}
```

### Render
#### Video
In the viewer under `Render`, create keyframes for camera path; adjust other parameters to taste.

You can preview and play your render before adding a render name and `Generate Command1` to create a render command.

#### GS
```
ns-export gaussian-splat --load-config {{outputs/[dataset-name]/[method]/[date]/config.yml} --output-dir [output-path]
```
or use
`ns-export gaussian-splat --help` for more information on GS export
