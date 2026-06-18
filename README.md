# MonoMDETR

**Depth-Ordered State-Space Query Interaction for Monocular 3D Object Detection**

MonoMDETR is a depth-guided state-space framework for monocular 3D object detection. It is built on the [MonoDETR](https://github.com/ZrrSkywalker/MonoDETR) detection pipeline and studies how depth cues can be used not only for final depth regression, but also for organizing object-query interaction inside the decoder.

This repository is currently in a staged release. At this stage, only the YAML configuration is public. The full implementation and reproducibility materials are being organized and will be released later.

## Release Status

| Item | Status |
| --- | --- |
| Main configuration: `configs/monodetr.yaml` | Available |
| Model code | Coming soon |
| Training and evaluation scripts | Coming soon |
| Pretrained checkpoints | Coming soon |
| Logs and diagnostic scripts | Coming soon |
| Paper / arXiv link | Coming soon |

The current YAML file is provided as a reference configuration. It is not enough to reproduce the reported results without the unreleased model implementation and training/evaluation code.


## Configuration

The main configuration is available at:

```text
configs/monodetr.yaml
```

Important settings in the current configuration include:

| Group | Setting |
| --- | --- |
| Dataset | KITTI |
| Category | Car |
| Backbone | ResNet-50 |
| Depth bins | 80 LID bins |
| Depth range | 0.1 m to 80.0 m |
| Decoder queries | 50 |
| Encoder / decoder layers | 3 / 3 |
| Optimizer | AdamW |
| Initial learning rate | 2e-4 |
| Training epochs | 195 |
| Main modules | DEEM and DC-Mamba enabled |

## Results

The following numbers are validation-set results on the KITTI Car category using AP at 40 recall positions. The MonoDETR baseline is reproduced locally under the same comparison protocol, using two NVIDIA RTX 4090 GPUs. These are controlled validation-split comparisons, not official KITTI test leaderboard claims.

| Method | 3D Easy | 3D Mod. | 3D Hard | BEV Easy | BEV Mod. | BEV Hard |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| MonoDETR baseline | 24.89 | 18.45 | 14.48 | 34.15 | 24.69 | 19.83 |
| MonoMDETR | 27.20 | 19.90 | 16.30 | 37.29 | 27.32 | 22.19 |

More detailed ablations, repeated-run analysis, complexity profiling, and diagnostic results will be released with the full code.

## Usage

Full installation, training, and evaluation instructions will be added after the implementation is released.

For now, the configuration can be inspected directly:

```bash
cat configs/monodetr.yaml
```

## Roadmap

- Release full MonoMDETR model implementation
- Release training and evaluation scripts
- Release pretrained checkpoints
- Release logs, ablation configs, and diagnostic scripts
- Add paper link and official citation

## Citation

The citation will be updated after the paper is publicly available.

If you use this repository, please also cite MonoDETR, since MonoMDETR is built on its depth-guided Transformer detection pipeline.

```bibtex
@misc{jiang2026monomdetr,
  title  = {Depth-Ordered State-Space Query Interaction for Monocular 3D Object Detection},
  author = {Jiang, Xiaoli and Jiang, Yunlong and Jin, Hangyu},
  year   = {2026},
  note   = {Manuscript in preparation}
}

@article{zhang2022monodetr,
  title   = {MonoDETR: Depth-guided Transformer for Monocular 3D Object Detection},
  author  = {Zhang, Renrui and Qiu, Han and Wang, Tai and Xu, Xuanzhuo and Guo, Ziyu and Qiao, Yu and Gao, Peng and Li, Hongsheng},
  journal = {ICCV 2023},
  year    = {2022}
}
```

## Acknowledgements

This project builds on the MonoDETR codebase and benefits from ideas and infrastructure from Deformable DETR, Mamba, and the KITTI 3D object detection benchmark. We thank the authors and maintainers of these projects and datasets.

## License

The license for the full release will be clarified when the implementation is made public.
