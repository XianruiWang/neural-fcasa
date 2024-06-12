<div align="center"><img src="https://raw.githubusercontent.com/b-sigpro/neural-fcasa/main/docs/image/logo.png" width="600"/></div>


# Neural Blind Source Separation and Diarization for Distant Speech Recognition
This is a repository of neural full-rank spatial covariance analysis with speaker activity (neural FCASA).
Neural FCASA is a method for jointly separating and diarizing speech mixtures without supervision by isolated signals.


## Installation
```bash
pip install git+https://github.com/b-sigpro/neural-fcasa.git
```

## Inference
### Using model pre-trained on the AMI corpus
```bash
python -m neural-fcasa.separate one hf://b-sigpro/neural-fcasa input.wav output.wav
```

### Genral usage
```bash
python -m neural-fcasa.separate one /path/to/model/ input.wav output.wav
```

The options are as follows:
* `--thresh`: Threshold to obtain diarization result (default: 0.5)
* `--out_ch`: Output channel index for Wiener filtering (default: 0)
* `--medfilt_size`: Filter size of median postfiltering (default: 11)
* `--dump_diar`: Dump diarization results as a pickle file (default: `false`)
* `--noi_snr`: SNR for white noise added to the separated result. No noise is added with `None`. (default: `None`)
* `--normalize`: Perform normalization of the separated result (default: `false`)
* `--device`: device type (e.g., `cuda` and `cpu`) for inference. (default: `cuda`)

We used the following configuration for the evaluation in the paper:
```bash
python -m neural-fcasa.separate one hf://b-sigpro/neural-fcasa --dump_diar --noi_snr=40 --normalize input.wav output.wav
```

## Traininig
The training script is compatible with PyTorch Lightning >= 2.2.3.
The training job file for ABCI is attatched on `recipes/neural-fcasa`.


## Reference
```bibtex
@inproceeding{bando2021neural,
  title={Neural Blind Source Separation and Diarization for Distant Speech Recognition},
  author={Yoshiaki Bando and Tomohiko Nakamura and Shinji Watanabe},
  booktitle={INTERSPEECH},
  year={2024}
}
```

## Acknowledgement
This work is based on results obtained from a project, Programs for Bridging the gap between R&D and the IDeal society (society 5.0) and Generating Economic and social value (BRIDGE)/Practical Global Research in the AI × Robotics Services, implemented by the Cabinet Office, Government of Japan.
