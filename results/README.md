# Local training evidence

Seven completed training runs were recovered from the locally saved Lightning checkpoints and CodeCarbon log. The raw checkpoints are not committed because several exceed GitHub's 100 MB per-file limit.

| Experiment | Best epoch | Validation loss | Validation balanced accuracy | Runtime | CO₂eq |
|---|---:|---:|---:|---:|---:|
| Baseline SmallCNN | 8 | 0.077 | 89.4% | 11m 39s | 0.000818 kg |
| Baseline SmallCNN rerun | 8 | 0.077 | 89.4% | 10m 29s | 0.000726 kg |
| SmallCNN, 32 px crop | 8 | 0.144 | 80.8% | 4m 10s | 0.000378 kg |
| SmallCNN, strict cloud filter | 5 | 0.126 | 67.1% | 4m 23s | 0.000302 kg |
| ImageNet ResNet50 | 4 | 0.368 | 74.0% | 10m 51s | 0.000700 kg |
| TorchGeo Sentinel-2 ResNet50 | 8 | 0.027 | 96.3% | 18m 17s | 0.001171 kg |
| SatlasPretrain ResNet50 | 0 | 0.320 | 50.0% | 1h 6m 28s | 0.003951 kg |

The machine-readable [training_runs.csv](training_runs.csv) records timestamps, checkpoint names, file sizes, CodeCarbon measurements, and SHA-256 hashes. Validation metrics come from Lightning's checkpoint filenames and callback state. Runtime, energy, and emissions values come from CodeCarbon. The manifest omits the raw CodeCarbon system and approximate-location fields.

When the local checkpoint directory is available, verify a model against the manifest with:

```bash
sha256sum models/<checkpoint-name>.ckpt
```
