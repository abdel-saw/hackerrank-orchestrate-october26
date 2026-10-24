# Google Colab free-tier experiments

Open the notebook directly:

https://colab.research.google.com/github/abdel-saw/hackerrank-orchestrate-october26/blob/work/code/colab/experiment.ipynb

Sign in to Google, save a copy to your Drive if desired, and run the cells in order. The notebook clones branch `work` into `/content/project`, installs the Python dependencies and Tesseract, and prepares the sample evidence. Select **Runtime → Change runtime type → GPU** before inference. Free-tier GPU availability and session duration vary; a paid subscription is not required by this workflow. If changing runtime resets your files, rerun setup.

The first model candidate is `Qwen/Qwen2.5-3B-Instruct`, loaded locally in 4-bit precision. Public weight downloads use Hugging Face with no API key, and the resolved model revision is recorded. Downloads require Internet, disk space and several GB of transfer. After download, the inference adapter loads local files only. No paid model APIs are used. This model's accuracy, VRAM use and speed on Colab remain unmeasured.

Set `USE_DRIVE = True` in the storage cell if you want caches and reports to survive a disconnect. This invokes Colab's ordinary Drive mount authorization; secrets do not belong in notebook cells. Otherwise files under `/content` are temporary: download results before ending the runtime. The notebook excludes model weights from its results archive. It is an experiment archive, not final `code.zip`.

The sample inference step can fail due to unsupported answers, malformed JSON, schema errors, context limits or GPU memory. Inspect `artifacts/sample/failures.json`, and evaluate this run's `partial_predictions.csv` to expose missing cases rather than hide them. A final sample CSV is written only when all selected cases validate. Response caches let reruns reuse completed generations. OCR success and schema validity do not prove correct policy reasoning.

The full 518-case run is opt-in (`RUN_FULL = True`) after you review sample errors. Keep its usage ledger distinct from the sample experiment. Do not evaluate it against sample labels or claim hidden accuracy. Read `code/KAGGLE.md` for the shared pipeline architecture, scoring definitions and remaining limitations; its platform-specific paths are superseded here by `/content` and optional Drive storage.

CPU preparation and ten software tests have been run in the development environment. Notebook source and structure are checked locally; package installation, model downloads and GPU inference must be verified in the actual Colab runtime. No hosted Colab session is available from this development environment.
