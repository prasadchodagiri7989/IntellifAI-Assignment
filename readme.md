# 🧠 LivePortrait Optimization – Assignment Submission

This repository contains:

- ✅ Original LivePortrait implementation
- ✅ Optimized version using `torch.compile()` and precision tweaks
- ✅ Performance benchmarks and timing analysis

---

## 🔧 Optimizations Applied

1. **Torch Compile Acceleration**
   - Used `torch.compile(model, mode='max-autotune')` in
     `LivePortraitWrapper` and `LivePortraitWrapperAnimal`
   - Models compiled:
     - `self.warping_module`
     - `self.spade_generator`

2. **Half-Precision Support**
   - Enabled `torch.autocast()` when `--flag_use_half_precision` is active
   - Reduced GPU memory usage for faster inference

3. **Data Type Safety Fix**
   - Ensured `.float()` is used after `.half()` in `helper.py` to avoid errors

4. **Inference Time Measurement**
   - Wrapped `subprocess.run(...)` with `time.time()` to calculate inference duration

---

## 🚀 Performance

| Version      | Inference Time |
|--------------|----------------|
| Original     | ~45 seconds    |
| Optimized    | ~42 seconds    |

> Minor but consistent improvement with safe optimizations and no architectural changes.

---

## 📌 Notes

- `inference.py` was **not modified**
- Optimization controlled via CLI flag `--flag_do_torch_compile`
