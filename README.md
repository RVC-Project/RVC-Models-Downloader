# RVC-Models-Downloader

English | [简体中文](README_sc.md) | [한국어](README_kr.md)

Easy tool to download a batch of files listed in yaml (ex. RVC models in Hugging Face 🤗).

![tui demo](https://github.com/fumiama/RVC-Models-Downloader/assets/41315874/db577dfb-8a6d-4909-b071-9d36cc77afc6)

## Quick Start

### Preparation

1. Download the program at [Release](https://github.com/fumiama/RVC-Models-Downloader/releases) page.
2. Put this program into the root directory of RVC (or whatever position you want to download some files into).
3. You can also add it to the `PATH` to use this tool everywhere. If you have installed this program by a package manager, it may be already in the `PATH`.

### Download

#### All Assets of RVC

```bash
rvcmd assets/rvc
```

#### All Assets of ChatTTS

```bash
rvcmd -w 1 assets/chtts
```

### Customized Download

#### Ex.1. Download hubert & rmvpe

1. Write and save the following `cust.yaml`.
    ```yaml
    BaseURL: https://huggingface.co/fumiama/RVC-Pretrained-Models/resolve/main
    Targets:
      - Refer: hubert
      - Refer: rmvpe
    ```
2. Run `rvcmd` in the same folder.
    ```bash
    rvcmd -c cust
    ```

#### Ex.2. Download other Repositories in 🤗

> Use [Stable Diffusion v1-5](https://huggingface.co/runwayml/stable-diffusion-v1-5) as the example.

1. Write and save the following `cust.yaml`.
    ```yaml
    BaseURL: https://huggingface.co/runwayml/stable-diffusion-v1-5/resolve/main
    Targets:
      - Folder: sd1.5 # the folder you want to download into
        Copy: # files to download
          - v1-5-pruned-emaonly.ckpt
          - v1-5-pruned-emaonly.safetensors
      - Folder: sd1.5/vae # the folder you want to download into
        Copy: # files to download
          - vae/diffusion_pytorch_model.bin
    ```

#### Ex.3. Download Releases in GitHub

> Use [yousa-ling-diffsinger-v1.3](https://github.com/yousa-ling-official-production/yousa-ling-diffsinger-v1/releases/tag/v1.3) as the example.

1. Write and save the following `cust.yaml`.
    ```yaml
    BaseURL: https://github.com/yousa-ling-official-production/yousa-ling-diffsinger-v1/releases/download/v1.3
    Targets:
      - Folder: . # the folder you want to download into
        Copy: # files to download
          - yousaV1.3.zip
    ```
2. Run `rvcmd` in the same folder.
    ```bash
    rvcmd -c cust
    ```

## Full Usage

```bash
Usage: rvcmd [-notrs] [-dns dns.yaml] 'target/to/download'
  -c    use custom yaml instruction
  -dns string
        custom dns.yaml
  -f    force download even file exists
  -notrs
        use standard TLS client
  -notui
        use plain text instead of TUI
  -ua string
        customize user agent (default "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36 Edg/123.0.0.0")
  -w uint
        connection waiting seconds (default 4)
  'target/to/download'
        like packs/general/latest
All available targets:
    assets:
        chtts    hubert    rmvpe    rvc    uvr5    v1    v2
```

## Demo Video

https://github.com/fumiama/RVC-Models-Downloader/assets/41315874/da2b5827-8b1a-45f8-a9c0-03a5618ad5f8
