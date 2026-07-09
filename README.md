# Team 19 (VIPSL) Code Package for NTIRE 2026 Mobile Real-World SR

Official reproducibility package for our NTIRE 2026 Mobile Real-World Image Super-Resolution submission (Team VIPSL #19).

## Paper

**PLKSR-Rep: A Compact Large-Kernel CNN for Mobile Real-World Image Super-Resolution**
JiaHao Deng, *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops*, 2026, pp. 1765-1773.

- https://openaccess.thecvf.com/content/CVPR2026W/NTIRE/papers/Deng_PLKSR-Rep_A_Compact_Large-Kernel_CNN_for_Mobile_Real-World_Image_Super-Resolution_CVPRW_2026_paper.pdf

If you use this code or build upon our method, please cite:

```bibtex
@InProceedings{Deng_2026_CVPR,
  author    = {Deng, JiaHao},
  title     = {PLKSR-Rep: A Compact Large-Kernel CNN for Mobile Real-World Image Super-Resolution},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  month     = {June},
  year      = {2026},
  pages     = {1765-1773}
}
```

## Repository Contents

- `plksr/` — model/network code
- `scripts/` — inference helper scripts
- `test.py` — inference entry
- `eval.py` — quick output format check
- `requirements.txt` — Python dependencies
- `LICENSE` — MIT license

> Note: Pretrained weights are hosted in **GitHub Releases** (not stored in repo tree due to file size limits).

## Environment

Tested with:

- Python 3.10
- PyTorch (CUDA)

Install dependencies:

```bash
pip install -r requirements.txt
```

## Pretrained Weights (Release Asset)

Release page:

- https://github.com/Innocentlove321/ntire2026-mobile-realworld-sr-vipsl19/releases/tag/ntire2026-final

Required checkpoint:

- `net_g_1000.pth`

Download and place into expected path:

```bash
mkdir -p model_zoo/19_PLKSRRep_IQAv2Short
wget -O model_zoo/19_PLKSRRep_IQAv2Short/net_g_1000.pth \
  "https://github.com/Innocentlove321/ntire2026-mobile-realworld-sr-vipsl19/releases/download/ntire2026-final/net_g_1000.pth"
```

## Run Inference

```bash
python test.py --input /path/to/test_LR --output /path/to/sr \
  --model_path model_zoo/19_PLKSRRep_IQAv2Short/net_g_1000.pth
```

Optional flags:

```bash
python test.py --input /path/to/test_LR --output /path/to/sr \
  --model_path model_zoo/19_PLKSRRep_IQAv2Short/net_g_1000.pth \
  --gpu 0 --fp16 0 --prepad 16
```

## Quick Output Check

```bash
python eval.py --input /path/to/test_LR --output /path/to/sr --scale 4
```

Expected:

- Output PNG filenames match input filenames
- Output resolution is exactly 4x input resolution

## Release Assets

The `ntire2026-final` release includes:

- `net_g_1000.pth` (pretrained checkpoint)
- `final_candidate_iqav2short_ckpt1000_test_fp32_20260317_113426.zip` (final FP32 output pack)
- `MobileSR_factsheet.pdf`
- `MobileSR_factsheet_source.zip`

## Notes

- Final scoring outputs are generated in FP32.
- Extra data used: **Yes**.

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE).

