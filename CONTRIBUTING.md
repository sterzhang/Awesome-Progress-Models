# Contributing

Contributions are welcome. If you find a relevant paper, codebase, or figure for **Progress Models**, please open a pull request and update [README.md](README.md) accordingly.

## What To Contribute

You can contribute:

- New papers related to progress models, progress reasoning, reward modeling, progress estimation, or closely related topics
- Missing code links
- Better preview images in `img/`
- Fixes for broken links, typos, duplicated entries, or formatting issues

## How To Add A Paper

Add the new entry to the `## 🔥 Methods` table in [README.md](README.md).

Use this template:

```markdown
| YYYY/MM | [Paper Title](https://arxiv.org/abs/xxxx.xxxxx) | <img width="320" alt="preview" src="img/your_image.png"> | [GitHub](https://github.com/your/repo) | <details><summary>bib.tex</summary><pre><code class="language-bibtex">@article{key,<br>  title={Paper Title},<br>  author={Author One and Author Two},<br>  journal={arXiv preprint arXiv:xxxx.xxxxx},<br>  year={2026}<br>}</code></pre></details> |
```

If there is no code release, use `-` in the `Code` column.

## Formatting Rules

- Keep the table sorted by date in descending order: newest papers first, oldest papers later.
- Use `YYYY/MM` in the `Date` column.
- Prefer the arXiv abstract page, for example `https://arxiv.org/abs/xxxx.xxxxx`, when an arXiv version exists.
- If a paper is published at a conference or journal, you may add a badge before the title, for example `![ICLR'24](https://img.shields.io/badge/ICLR'24-f1b800)`.
- Put the preview image under `img/` and reference it with a relative path such as `img/2604_arm.png`.
- Keep preview images clean and readable. Avoid images with excessive blank space or unreadable text.
- Keep the `Citation` column on a single table row. Use `<details><summary>bib.tex</summary><pre><code ...>...</code></pre></details>` and use `<br>` for line breaks inside the bib entry.
- Follow the existing capitalization style for link labels. `GitHub` is preferred.

## Before Submitting

Please check the following before opening a pull request:

- The paper is relevant to the scope of this repository.
- The entry is inserted at the correct position by date.
- The title link works.
- The image path works and the image renders in the table.
- The citation block expands correctly and does not break the Markdown table.
- The paper is not already listed in the table.

## Example Entries

Example without venue badge:

```markdown
| 2026/04 | [ARM: Advantage Reward Modeling for Long-Horizon Manipulation](https://arxiv.org/abs/2604.03037) | <img width="320" alt="preview" src="img/2604_arm.png"> | - | <details><summary>bib.tex</summary><pre><code class="language-bibtex">@misc{mao2026armadvantagerewardmodeling,<br>  title={ARM: Advantage Reward Modeling for Long-Horizon Manipulation},<br>  author={Yiming Mao and Zixi Yu and Weixin Mao and Yinhao Li and Qirui Hu and Zihan Lan and Minzhao Zhu and Hua Chen},<br>  year={2026},<br>  eprint={2604.03037},<br>  archivePrefix={arXiv},<br>  primaryClass={cs.RO},<br>  url={https://arxiv.org/abs/2604.03037},<br>}</code></pre></details> |
```

Example with venue badge:

```markdown
| 2025/12 | ![CVPR'26](https://img.shields.io/badge/CVPR'26-f1b800) <br/> [Robo-Dopamine: General Process Reward Modeling for High-Precision Robotic Manipulation](https://arxiv.org/abs/2512.23703) | <img width="700" alt="image" src="img/2512_robo_dopamine.png"> | [GitHub](https://github.com/FlagOpen/Robo-Dopamine) | <details><summary>bib.tex</summary><pre><code class="language-bibtex">@article{tan2025robo,<br>  title={Robo-Dopamine: General Process Reward Modeling for High-Precision Robotic Manipulation},<br>  author={Tan, Huajie and Chen, Sixiang and Xu, Yijie and Wang, Zixiao and Ji, Yuheng and Chi, Cheng and Lyu, Yaoxu and Zhao, Zhongxia and Chen, Xiansheng and Co, Peterson and Xie, Shaoxuan and Yao, Guocai and Wang, Pengwei and Wang, Zhongyuan and Zhang, Shanghang},<br>  journal={arXiv preprint arXiv:2512.23703},<br>  year={2025}<br>}</code></pre></details> |
```

## Notes

- Small fixes are also welcome. You do not need to contribute a full new paper entry.
- If you are unsure whether a paper fits the scope, open an issue or draft pull request first.
