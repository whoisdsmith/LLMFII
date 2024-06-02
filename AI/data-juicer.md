# Data Juicer

---

[[]](https://github.com/modelscope/data-juicer/blob/main/README_ZH.md) | [[docs]](https://github.com/modelscope/data-juicer#documents) | [[API]](https://modelscope.github.io/data-juicer) | [[*DJ-SORA*]](https://github.com/modelscope/data-juicer/blob/main/docs/DJ_SORA.md)

## Data-Juicer: A One-Stop Data Processing System for Large Language Models

[![Data-Juicer](https://camo.githubusercontent.com/8646b0e08981277ffc03d19c0a939b8fc4a487ad20c230c63975c7dba5915c88/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69332f4f31434e3031374571356b663237416c41324e554b65665f2121363030303030303030373735372d302d7470732d313238302d3732302e6a7067)](https://camo.githubusercontent.com/8646b0e08981277ffc03d19c0a939b8fc4a487ad20c230c63975c7dba5915c88/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69332f4f31434e3031374571356b663237416c41324e554b65665f2121363030303030303030373735372d302d7470732d313238302d3732302e6a7067)

[![](https://camo.githubusercontent.com/2775ee0bc040b7f60abdd38039a391f8ab08caf19841002ab4e5ad0a0cc187c6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c616e67756167652d507974686f6e2d3231343837302e737667)](https://camo.githubusercontent.com/2775ee0bc040b7f60abdd38039a391f8ab08caf19841002ab4e5ad0a0cc187c6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c616e67756167652d507974686f6e2d3231343837302e737667) [![](https://camo.githubusercontent.com/cee87edf1f68adb15105bbc929d804c8ac3af1fa1940c6b7f9cda1c3e93f4f9f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4170616368652d2d322e302d3030303030302e737667)](https://camo.githubusercontent.com/cee87edf1f68adb15105bbc929d804c8ac3af1fa1940c6b7f9cda1c3e93f4f9f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4170616368652d2d322e302d3030303030302e737667) [![pypi version](https://camo.githubusercontent.com/8b772f53d84c6e9aab32bc8c0de588a21d92597c24a1a809b135923047da0933/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f70792d646174612d6a75696365723f6c6f676f3d7079706926636f6c6f723d303236636164)](https://pypi.org/project/py-data-juicer) [![Docker version](https://camo.githubusercontent.com/c5510bf6799e43afebebf548689c02a34db0044bbb25bb51a21d86434fda66b4/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f762f646174616a75696365722f646174612d6a75696365723f6c6f676f3d646f636b6572266c6162656c3d446f636b657226636f6c6f723d343938626466)](https://hub.docker.com/r/datajuicer/data-juicer)

[![DataModality](https://camo.githubusercontent.com/766e6186495d7dee43b0a843bab86c22d65525a36e953194a442d5f4304fdf1a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446174614d6f64616c6974792d546578742c496d6167652c417564696f2c566964656f2d627269676874677265656e2e737667)](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide_ZH.md) [![Usage](https://camo.githubusercontent.com/368d68bb1f535c56fc3bbfd6d8a28d52ff9d8d743f2374c8281c228506f25735/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f55736167652d436c65616e696e672c47656e65726174696f6e2c416e616c797369732d4646443231452e737667)](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide_ZH.md) [![ModelScope- Demos](https://camo.githubusercontent.com/4c2e9350ccf2686cadc8a49fa11c69103ef4a016c3a49891beda448cdbd0af0a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4d6f64656c53636f70652d44656d6f732d3465323966662e7376673f6c6f676f3d646174613a696d6167652f7376672b786d6c3b6261736536342c50484e325a79423261575633516d393450534977494441674d6a4930494445794d53347a4d79496765473173626e4d39496d6830644841364c79393364336375647a4d7562334a6e4c7a49774d44417663335a6e496a344b435478775958526f49475139496d3077494451334c6a6730614449314c6a5931646a49314c6a5931614330794e5334324e586f6949475a706247773949694d324d6a52685a6d59694943382b43676b38634746306143426b50534a744f546b754d5451674e7a4d754e446c6f4d6a55754e6a56324d6a55754e6a566f4c5449314c6a5931656949675a6d6c7362443069497a59794e47466d5a6949674c7a344b435478775958526f49475139496d30784e7a59754d446b674f546b754d54526f4c5449314c6a5931646a49794c6a4535614451334c6a6730646930304e7934344e4767744d6a49754d546c364969426d615778735053496a4e6a493059575a6d4969417650676f4a50484268644767675a443069625445794e4334334f5341304e7934344e4767794e5334324e5859794e5334324e5767744d6a55754e6a56364969426d615778735053496a4d7a5a6a5a6d51784969417650676f4a50484268644767675a443069625441674d6a49754d546c6f4d6a55754e6a56324d6a55754e6a566f4c5449314c6a5931656949675a6d6c7362443069497a4d3259325a6b4d5349674c7a344b435478775958526f49475139496d30784f5467754d6a67674e4463754f44526f4d6a55754e6a56324d6a55754e6a566f4c5449314c6a5931656949675a6d6c7362443069497a59794e47466d5a6949674c7a344b435478775958526f49475139496d30784f5467754d6a67674d6a49754d546c6f4d6a55754e6a56324d6a55754e6a566f4c5449314c6a5931656949675a6d6c7362443069497a4d3259325a6b4d5349674c7a344b435478775958526f49475139496d30784e5441754e4451674d4859794d6934784f5767794e5334324e5859794e5334324e5767794d6934784f5859744e4463754f4452364969426d615778735053496a4e6a493059575a6d4969417650676f4a50484268644767675a4430696254637a4c6a5135494451334c6a6730614449314c6a5931646a49314c6a5931614330794e5334324e586f6949475a706247773949694d7a4e6d4e6d5a4445694943382b43676b38634746306143426b50534a744e4463754f4451674d6a49754d546c6f4d6a55754e6a56324c5449794c6a4535614330304e7934344e4859304e7934344e4767794d6934784f586f6949475a706247773949694d324d6a52685a6d59694943382b43676b38634746306143426b50534a744e4463754f4451674e7a4d754e446c6f4c5449794c6a4535646a51334c6a6730614451334c6a6730646930794d6934784f5767744d6a55754e6a56364969426d615778735053496a4e6a493059575a6d4969417650676f384c334e325a7a344b)](https://modelscope.cn/studios?name=Data-Jiucer&page=1&sort=latest&type=1) [![HuggingFace- Demos](https://camo.githubusercontent.com/43d908a3cbec729048c9229e78ae8e96c997970c31b3093abab676dd2f57f391/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f25463025394625413425393748756767696e67466163652d44656d6f732d3465323966662e737667)](https://huggingface.co/spaces?&search=datajuicer)

[![Document_List](https://camo.githubusercontent.com/7e9b2b2e0c112f202ab757e57e133c245ea173064b00a2ee32837fe30d05acce/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f63732d456e676c6973682d626c75653f6c6f676f3d4d61726b646f776e)](https://github.com/modelscope/data-juicer#documents) [![](https://camo.githubusercontent.com/667fe14c560ee621e48344a8c62d91fd3b8e390a56398a97aae632742d2d1f91/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2545362539362538372545362541312541332d2545342542382541442545362539362538372d626c75653f6c6f676f3d4d61726b646f776e)](https://github.com/modelscope/data-juicer/blob/main/README_ZH.md#documents) [![API Reference](https://camo.githubusercontent.com/451e2b712db7d5d10151256c28df17811aa60f166ea3737193d50e785c39b07f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f63732d4150495f5265666572656e63652d626c75653f6c6f676f3d4d61726b646f776e)](https://modelscope.github.io/data-juicer/) [![Paper](https://camo.githubusercontent.com/0a229f6ae05c2ccbd804b8202fc8cc3c1fd6cd093d3410585a442eee6ebc3ebb/687474703a2f2f696d672e736869656c64732e696f2f62616467652f63732e4c472d6172586976253341323330392e30323033332d4233314231423f6c6f676f3d6172786976266c6f676f436f6c6f723d726564)](https://arxiv.org/abs/2309.02033)

Data-Juicer is a one-stop **multimodal** data processing system to make data higher-quality, juicier, and more digestible for LLMs.

Data-Juicer (including [DJ-SORA](https://github.com/modelscope/data-juicer/blob/main/docs/DJ_SORA.md)) is being actively updated and maintained. We will periodically enhance and add more features, data recipes and datasets. We welcome you to join us in promoting LLM data development and research!

We provide a [Playground](http://8.130.100.170/) with a managed JupyterLab. [Try Data-Juicer](http://8.130.100.170/) straight away in your browser!

If you find Data-Juicer useful for your research or development, please kindly cite our [work](https://github.com/modelscope/data-juicer#references). Welcome any issues/PRs and to join our [Slack channel](https://join.slack.com/t/data-juicer/shared_invite/zt-23zxltg9d-Z4d3EJuhZbCLGwtnLWWUDg?spm=a2c22.12281976.0.0.7a8253f30mgpjw) or [DingDing group](https://qr.dingtalk.com/action/joingroup?spm=a2c22.12281976.0.0.7a8253f30mgpjw&code=v1,k1,C0DI7CwRFrg7gJP5aMC95FUmsNuwuKJboT62BqP5DAk=&_dt_no_comment=1&origin=11) for discussion!

---

## News

- [![new](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67)](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67) [2024-03-07] We release **Data-Juicer [v0.2.0](https://github.com/alibaba/data-juicer/releases/tag/v0.2.0)** now! In this new version, we support more features for **multimodal data (including video now)**, and introduce **[DJ-SORA](https://github.com/modelscope/data-juicer/blob/main/docs/DJ_SORA.md)** to provide open large-scale, high-quality datasets for SORA-like models.

- [![new](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67)](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67) [2024-02-20] We have actively maintained an *awesome list of LLM-Data*, welcome to [visit](https://github.com/modelscope/data-juicer/blob/main/docs/awesome_llm_data.md) and contribute!

- [![new](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67)](https://camo.githubusercontent.com/7eee5e036746568e41cf07e71d2005db472d0ccabc2ed1df5ac6a0257df34f76/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e30316b556944746c314856784e36473536764e5f2121363030303030303030303736342d322d7470732d34332d31392e706e67) [2024-02-05] Our paper has been accepted by SIGMOD'24 industrial track!

- [2024-01-10] Discover new horizons in "Data Mixture"—Our second data-centric LLM competition has kicked off! Please visit the competition's [official website](https://tianchi.aliyun.com/competition/entrance/532174) for more information.

- [2024-01-05] We release **Data-Juicer v0.1.3** now! In this new version, we support **more Python versions** (3.8-3.10), and support **multimodal** dataset [converting](https://github.com/modelscope/data-juicer/blob/main/tools/multimodal/README.md)/[processing](https://github.com/modelscope/data-juicer/blob/main/docs/Operators.md) (Including texts, images, and audios. More modalities will be supported in the future). Besides, our paper is also updated to [v3](https://arxiv.org/abs/2309.02033).

- [2023-10-13] Our first data-centric LLM competition begins! Please visit the competition's official websites, FT-Data Ranker ([1B Track](https://tianchi.aliyun.com/competition/entrance/532157), [7B Track](https://tianchi.aliyun.com/competition/entrance/532158)), for more information.

- [2023-10-8] We update our paper to the 2nd version and release the corresponding version 0.1.2 of Data-Juicer!


## Table of Contents

- [Data-Juicer: A One-Stop Data Processing System for Large Language Models](https://github.com/modelscope/data-juicer#data-juicer--a-one-stop-data-processing-system-for-large-language-models)
    - [News](https://github.com/modelscope/data-juicer#news)
- [Table of Contents](https://github.com/modelscope/data-juicer#table-of-contents)
    - [Features](https://github.com/modelscope/data-juicer#features)
    - [Documentation Index](https://github.com/modelscope/data-juicer#documentation-index-)
    - [Demos](https://github.com/modelscope/data-juicer#demos)
    - [Prerequisites](https://github.com/modelscope/data-juicer#prerequisites)
    - [Installation](https://github.com/modelscope/data-juicer#installation)
        - [From Source](https://github.com/modelscope/data-juicer#from-source)
        - [Using pip](https://github.com/modelscope/data-juicer#using-pip)
        - [Using Docker](https://github.com/modelscope/data-juicer#using-docker)
        - [Installation check](https://github.com/modelscope/data-juicer#installation-check)
    - [Quick Start](https://github.com/modelscope/data-juicer#quick-start)
        - [Data Processing](https://github.com/modelscope/data-juicer#data-processing)
        - [Distributed Data Processing](https://github.com/modelscope/data-juicer#distributed-data-processing)
        - [Data Analysis](https://github.com/modelscope/data-juicer#data-analysis)
        - [Data Visualization](https://github.com/modelscope/data-juicer#data-visualization)
        - [Build Up Config Files](https://github.com/modelscope/data-juicer#build-up-config-files)
        - [Sandbox](https://github.com/modelscope/data-juicer#sandbox)
        - [Preprocess Raw Data (Optional)](https://github.com/modelscope/data-juicer#preprocess-raw-data-optional)
        - [For Docker Users](https://github.com/modelscope/data-juicer#for-docker-users)
    - [Data Recipes](https://github.com/modelscope/data-juicer#data-recipes)
    - [License](https://github.com/modelscope/data-juicer#license)
    - [Contributing](https://github.com/modelscope/data-juicer#contributing)
    - [Acknowledgement](https://github.com/modelscope/data-juicer#acknowledgement)
    - [References](https://github.com/modelscope/data-juicer#references)

## Features

[![Overview](https://camo.githubusercontent.com/79463a6defffd61aa6c19b14d88250f8cdbb01551a5bcf0667697c52a580d4ce/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e303157595150335a314a487361586151444b365f2121363030303030303030313030342d302d7470732d333634302d313831322e6a7067)](https://camo.githubusercontent.com/79463a6defffd61aa6c19b14d88250f8cdbb01551a5bcf0667697c52a580d4ce/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e303157595150335a314a487361586151444b365f2121363030303030303030313030342d302d7470732d333634302d313831322e6a7067)

- **Systematic & Reusable**: Empowering users with a systematic library of 80+ core [OPs](https://github.com/modelscope/data-juicer/blob/main/docs/Operators.md), 20+ reusable [config recipes](https://github.com/modelscope/data-juicer/blob/main/configs), and 20+ feature-rich dedicated [toolkits](https://github.com/modelscope/data-juicer#documentation), designed to function independently of specific multimodal LLM datasets and processing pipelines.

- **Data-in-the-loop & Sandbox**: Supporting one-stop data-model collaborative development, enabling rapid iteration through the [sandbox laboratory](https://github.com/modelscope/data-juicer/blob/main/docs/Sandbox.md), and providing features such as feedback loops based on data and model, visualization, and multidimensional automatic evaluation, so that you can better understand and improve your data and models. [![Data-in-the-loop](https://camo.githubusercontent.com/4509a541c52f2a89ef2fe858858b3f1534e78673429ebffeeae34bcd101c67b4/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69322f4f31434e30313755375a7a333159375874434a35474f7a5f2121363030303030303030333031322d302d7470732d333634302d313536372e6a7067)](https://camo.githubusercontent.com/4509a541c52f2a89ef2fe858858b3f1534e78673429ebffeeae34bcd101c67b4/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69322f4f31434e30313755375a7a333159375874434a35474f7a5f2121363030303030303030333031322d302d7470732d333634302d313536372e6a7067)

- **Enhanced Efficiency**: Providing efficient and parallel data processing pipelines (Aliyun-PAI\Ray\Slurm\CUDA\OP Fusion) requiring less memory and CPU usage, optimized for maximum productivity. [![sys-perf](https://camo.githubusercontent.com/59f1fd43e755e90b8f4fbb4a5cf74fb58bda1158e7626d64368df637aae26fc5/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e3031536b307132553168645278626e515846675f2121363030303030303030343330302d302d7470732d323433382d3730392e6a7067)](https://camo.githubusercontent.com/59f1fd43e755e90b8f4fbb4a5cf74fb58bda1158e7626d64368df637aae26fc5/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69342f4f31434e3031536b307132553168645278626e515846675f2121363030303030303030343330302d302d7470732d323433382d3730392e6a7067)

- **Comprehensive Data Processing Recipes**: Offering tens of [pre-built data processing recipes](https://github.com/modelscope/data-juicer/blob/main/configs/data_juicer_recipes/README.md) for pre-training, fine-tuning, en, zh, and more scenarios. Validated on reference LLaMA and LLaVA models. [![exp_llama](https://camo.githubusercontent.com/5bbcb2b2eb5346c2196f5e3ca4af67de3191459b93849b54a52faa42c57f0158/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69322f4f31434e303139577455505031756865626e446c5052385f2121363030303030303030363036392d322d7470732d323533302d313030352e706e67)](https://camo.githubusercontent.com/5bbcb2b2eb5346c2196f5e3ca4af67de3191459b93849b54a52faa42c57f0158/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69322f4f31434e303139577455505031756865626e446c5052385f2121363030303030303030363036392d322d7470732d323533302d313030352e706e67)

- **Flexible & Extensible**: Accommodating most types of data formats (e.g., jsonl, parquet, csv, ...) and allowing flexible combinations of OPs. Feel free to [implement your own OPs](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide.md#build-your-own-ops) for customizable data processing.

- **User-Friendly Experience**: Designed for simplicity, with [comprehensive documentation](https://github.com/modelscope/data-juicer#documents), [easy start guides](https://github.com/modelscope/data-juicer#quick-start) and [demo configs](https://github.com/modelscope/data-juicer/blob/main/configs/README.md), and intuitive configuration with simple adding/removing OPs from [existing configs](https://github.com/modelscope/data-juicer/blob/main/configs/config_all.yaml).


## Documentation Index

- [Overview](https://github.com/modelscope/data-juicer/blob/main/README.md)
- [Operator Zoo](https://github.com/modelscope/data-juicer/blob/main/docs/Operators.md)
- [Configs](https://github.com/modelscope/data-juicer/blob/main/configs/README.md)
- [Developer Guide](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide.md)
- ["Bad" Data Exhibition](https://github.com/modelscope/data-juicer/blob/main/docs/BadDataExhibition.md)
- Dedicated Toolkits
    - [Quality Classifier](https://github.com/modelscope/data-juicer/blob/main/tools/quality_classifier/README.md)
    - [Auto Evaluation](https://github.com/modelscope/data-juicer/blob/main/tools/evaluator/README.md)
    - [Preprocess](https://github.com/modelscope/data-juicer/blob/main/tools/preprocess/README.md)
    - [Postprocess](https://github.com/modelscope/data-juicer/blob/main/tools/postprocess/README.md)
- [Third-parties (LLM Ecosystems)](https://github.com/modelscope/data-juicer/blob/main/thirdparty/README.md)
- [API references](https://modelscope.github.io/data-juicer/)
- [Awesome LLM-Data](https://github.com/modelscope/data-juicer/blob/main/docs/awesome_llm_data.md)
- [DJ-SORA](https://github.com/modelscope/data-juicer/blob/main/docs/DJ_SORA.md)

## Demos

- Introduction to Data-Juicer [[ModelScope](https://modelscope.cn/studios/Data-Juicer/overview_scan/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/overview_scan)]
- Data Visualization:
    - Basic Statistics [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_visulization_statistics/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_visualization_statistics)]
    - Lexical Diversity [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_visulization_diversity/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_visualization_diversity)]
    - Operator Insight (Single OP) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_visualization_op_insight/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_visualization_op_insight)]
    - Operator Effect (Multiple OPs) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_visulization_op_effect/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_visualization_op_effect)]
- Data Processing:
    - Scientific Literature (e.g. [arXiv](https://info.arxiv.org/help/bulk_data_s3.html)) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/process_sci_data/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/process_sci_data)]
    - Programming Code (e.g. [TheStack](https://huggingface.co/datasets/bigcode/the-stack)) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/process_code_data/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/process_code_data)]
    - Chinese Instruction Data (e.g. [Alpaca-CoT](https://huggingface.co/datasets/QingyiSi/Alpaca-CoT)) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/process_sft_zh_data/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/process_cft_zh_data)]
- Tool Pool:
    - Dataset Splitting by Language [[ModelScope](https://modelscope.cn/studios/Data-Juicer/tool_dataset_splitting_by_language/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/tool_dataset_splitting_by_language)]
    - Quality Classifier for CommonCrawl [[ModelScope](https://modelscope.cn/studios/Data-Juicer/tool_quality_classifier/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/tool_quality_classifier)]
    - Auto Evaluation on [HELM](https://github.com/stanford-crfm/helm) [[ModelScope](https://modelscope.cn/studios/Data-Juicer/auto_evaluation_helm/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/auto_evaluation_helm)]
    - Data Sampling and Mixture [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_mixture/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_mixture)]
- Data Processing Loop [[ModelScope](https://modelscope.cn/studios/Data-Juicer/data_process_loop/summary)] [[HuggingFace](https://huggingface.co/spaces/datajuicer/data_process_loop)]

## Prerequisites

- Recommend Python>=3.8,<=3.10
- gcc >= 5 (at least C++14 support)

## Installation

### From Source

- Run the following commands to install the latest basic `data_juicer` version in editable mode:

```shell
cd <path_to_data_juicer>
pip install -v -e .
```

- Some OPs rely on some other too large or low-platform-compatibility third-party libraries. You can install optional dependencies as needed:

```shell
cd <path_to_data_juicer>
pip install -v -e .  # install a minimal dependencies, which support the basic functions
pip install -v -e .[tools] # install a subset of tools dependencies
```

The dependency options are listed below:

| Tag | Description |
| --- | --- |
| `.` or `.[mini]` | Install minimal dependencies for basic Data-Juicer. |
| `.[all]` | Install all dependencies except sandbox. |
| `.[sci]` | Install all dependencies for all OPs. |
| `.[dist]` | Install dependencies for distributed data processing. (Experimental) |
| `.[dev]` | Install dependencies for developing the package as contributors. |
| `.[tools]` | Install dependencies for dedicated tools, such as quality classifiers. |
| `.[sandbox]` | Install all dependencies for sandbox. |

### Using Pip

- Run the following command to install the latest released `data_juicer` using `pip`:

```shell
pip install py-data-juicer
```

- **Note**:
    - only the basic APIs in `data_juicer` and two basic tools (data [processing](https://github.com/modelscope/data-juicer#data-processing) and [analysis](https://github.com/modelscope/data-juicer#data-analysis)) are available in this way. If you want customizable and complete functions, we recommend you install `data_juicer` [from source](https://github.com/modelscope/data-juicer#from-source).
    - The release versions from pypi have a certain lag compared to the latest version from source. So if you want to follow the latest functions of `data_juicer`, we recommend you install [from source](https://github.com/modelscope/data-juicer#from-source).

### Using Docker

- You can
    - either pull our pre-built image from DockerHub:

        ```shell
        docker pull datajuicer/data-juicer:<version_tag>
        ```

    - or run the following command to build the docker image including the latest `data-juicer` with provided [Dockerfile](https://github.com/modelscope/data-juicer/blob/main/Dockerfile):

        ```shell
        docker build -t datajuicer/data-juicer:<version_tag> .
        ```

    - The format of `<version_tag>` is like `v0.2.0`, which is the same as release version tag.


### Installation Check

```python
import data_juicer as dj
print(dj.__version__)
```

### For Video-related Operators

Before using video-related operators, **FFmpeg** should be installed and accessible via the $PATH environment variable.

You can install FFmpeg using package managers(e.g. sudo apt install ffmpeg on Debian/Ubuntu, brew install ffmpeg on OS X) or visit the [offical ffmpeg link](https://ffmpeg.org/download.html).

Check if your environment path is set correctly by running the ffmpeg command from the terminal.

## Quick Start

### Data Processing

- Run `process_data.py` tool or `dj-process` command line tool with your config as the argument to process your dataset.

```shell
# only for installation from source
python tools/process_data.py --config configs/demo/process.yaml

# use command line tool
dj-process --config configs/demo/process.yaml
```

- **Note:** For some operators that involve third-party models or resources which are not stored locally on your computer, it might be slow for the first running because these ops need to download corresponding resources into a directory first. The default download cache directory is `~/.cache/data_juicer`. Change the cache location by setting the shell environment variable, `DATA_JUICER_CACHE_HOME` to another directory, and you can also change `DATA_JUICER_MODELS_CACHE` or `DATA_JUICER_ASSETS_CACHE` in the same way:

- **Note:** When using operators with third-party models, it's necessary to declare the corresponding `mem_required` in the configuration file (you can refer to the settings in the `config_all.yaml` file). During runtime, Data-Juicer will control the number of processes based on memory availability and the memory requirements of the operator models to achieve better data processing efficiency. When running with CUDA environment, if the mem_required for an operator is not declared correctly, it could potentially lead to a CUDA Out of Memory issue.


```shell
# cache home
export DATA_JUICER_CACHE_HOME="/path/to/another/directory"
# cache models
export DATA_JUICER_MODELS_CACHE="/path/to/another/directory/models"
# cache assets
export DATA_JUICER_ASSETS_CACHE="/path/to/another/directory/assets"
```

### Distributed Data Processing

We have now implemented multi-machine distributed data processing based on [RAY](https://www.ray.io/). The corresponding demos can be run using the following commands:

```shell
# Run text data processing
python tools/process_data.py --config ./demos/process_on_ray/configs/demo.yaml
# Run video data processing
python tools/process_data.py --config ./demos/process_video_on_ray/configs/demo.yaml
```

- To run data processing across multiple machines, it is necessary to ensure that all distributed nodes can access the corresponding data paths (for example, by mounting the respective data paths on a file-sharing system such as NAS).
- The deduplicator operators for RAY mode are different from the single-machine version, and all those operators are prefixed with `ray`, e.g. `ray_video_deduplicator` and `ray_document_deduplicator`. Those operators also rely on a [Redis](https://redis.io/) instance. So in addition to starting the RAY cluster, you also need to setup your Redis instance in advance and provide `host` and `port` of your Redis instance in configuration.

> Users can also opt not to use RAY and instead split the dataset to run on a cluster with [Slurm](https://slurm.schedmd.com/) / [Aliyun PAI-DLC](https://www.aliyun.com/activity/bigdata/pai-dlc). In this case, please use the default Data-Juicer without RAY.

### Data Analysis

- Run `analyze_data.py` tool or `dj-analyze` command line tool with your config as the argument to analyse your dataset.

```shell
# only for installation from source
python tools/analyze_data.py --config configs/demo/analyser.yaml

# use command line tool
dj-analyze --config configs/demo/analyser.yaml
```

- **Note:** Analyser only compute stats of Filter ops. So extra Mapper or Deduplicator ops will be ignored in the analysis process.

### Data Visualization

- Run `app.py` tool to visualize your dataset in your browser.
- **Note**: only available for installation from source.

### Build Up Config Files

- Config files specify some global arguments, and an operator list for the data process. You need to set:
    - Global arguments: input/output dataset path, number of workers, etc.
    - Operator list: list operators with their arguments used to process the dataset.
- You can build up your own config files by:
    - ➖：Modify from our example config file [`config_all.yaml`](https://github.com/modelscope/data-juicer/blob/main/configs/config_all.yaml) which includes **all** ops and default arguments. You just need to **remove** ops that you won't use and refine some arguments of ops.
    - ➕：Build up your own config files **from scratch**. You can refer our example config file [`config_all.yaml`](https://github.com/modelscope/data-juicer/blob/main/configs/config_all.yaml), [op documents](https://github.com/modelscope/data-juicer/blob/main/docs/Operators.md), and advanced [Build-Up Guide for developers](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide.md#build-your-own-configs).
    - Besides the yaml files, you also have the flexibility to specify just one (of several) parameters on the command line, which will override the values in yaml files.

```shell
python xxx.py --config configs/demo/process.yaml --language_id_score_filter.lang=en
```

- The basic config format and definition is shown below.

    [![Basic config example of format and definition](https://camo.githubusercontent.com/4014c312c16c514ab33abbee4f9027f9dfdc0caebe42af8a1599a51a6637242d/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69312f4f31434e30317558676a676a316b68574b4f69675977775f2121363030303030303030343731352d302d7470732d313734352d3837312e6a7067 "Basic config file example")](https://camo.githubusercontent.com/4014c312c16c514ab33abbee4f9027f9dfdc0caebe42af8a1599a51a6637242d/68747470733a2f2f696d672e616c6963646e2e636f6d2f696d6765787472612f69312f4f31434e30317558676a676a316b68574b4f69675977775f2121363030303030303030343731352d302d7470732d313734352d3837312e6a7067)


### Sandbox

The data sandbox laboratory (DJ-Sandbox) provides users with the best practices for continuously producing data recipes. It features low overhead, portability, and guidance.

- In the sandbox, users can quickly experiment, iterate, and refine data recipes based on small-scale datasets and models, before scaling up to produce high-quality data to serve large-scale models.
- In addition to the basic data optimization and recipe refinement features offered by Data-Juicer, users can seamlessly use configurable components such as data probe and analysis, model training and evaluation, and data and model feedback-based recipe refinement to form a complete one-stop data-model research and development pipeline.

The sandbox is run using the following commands by default, and for more information and details, please refer to the [sandbox documentation](https://github.com/modelscope/data-juicer/blob/main/docs/Sandbox.md).

```shell
python tools/sandbox_starter.py --config configs/demo/sandbox/sandbox.yaml
```

### Preprocess Raw Data (Optional)

- Our formatters support some common input dataset formats for now:
    - Multi-sample in one file: jsonl/json, parquet, csv/tsv, etc.
    - Single-sample in one file: txt, code, docx, pdf, etc.
- However, data from different sources are complicated and diverse. Such as:
    - [Raw arXiv data downloaded from S3](https://info.arxiv.org/help/bulk_data_s3.html) include thousands of tar files and even more gzip files in them, and expected tex files are embedded in the gzip files so they are hard to obtain directly.
    - Some crawled data include different kinds of files (pdf, html, docx, etc.). And extra information like tables, charts, and so on is hard to extract.
- It's impossible to handle all kinds of data in Data-Juicer, issues/PRs are welcome to contribute to process new data types!
- Thus, we provide some **common preprocessing tools** in [`tools/preprocess`](https://github.com/modelscope/data-juicer/blob/main/tools/preprocess) for you to preprocess these data.
    - You are welcome to make your contributions to new preprocessing tools for the community.
    - We **highly recommend** that complicated data can be preprocessed to jsonl or parquet files.

### For Docker Users

- If you build or pull the docker image of `data-juicer`, you can run the commands or tools mentioned above using this docker image.
- Run directly:

```shell
# run the data processing directly
docker run --rm \  # remove container after the processing
  --name dj \  # name of the container
  -v <host_data_path>:<image_data_path> \  # mount data or config directory into the container
  -v ~/.cache/:/root/.cache/ \  # mount the cache directory into the container to reuse caches and models (recommended)
  datajuicer/data-juicer:<version_tag> \  # image to run
  dj-process --config /path/to/config.yaml  # similar data processing commands
```

- Or enter into the running container and run commands in editable mode:

```shell
# start the container
docker run -dit \  # run the container in the background
  --rm \
  --name dj \
  -v <host_data_path>:<image_data_path> \
  -v ~/.cache/:/root/.cache/ \
  datajuicer/data-juicer:latest /bin/bash

# enter into this container and then you can use data-juicer in editable mode
docker exec -it <container_id> bash
```

## Data Recipes

- [Recipes for data process in BLOOM](https://github.com/modelscope/data-juicer/blob/main/configs/reproduced_bloom/README.md)
- [Recipes for data process in RedPajama](https://github.com/modelscope/data-juicer/blob/main/configs/redpajama/README.md)
- [Refined recipes for pre-training text data](https://github.com/modelscope/data-juicer/blob/main/configs/data_juicer_recipes/README.md)
- [Refined recipes for fine-tuning text data](https://github.com/modelscope/data-juicer/blob/main/configs/data_juicer_recipes/README.md#before-and-after-refining-for-alpaca-cot-dataset)
- [Refined recipes for pre-training multi-modal data](https://github.com/modelscope/data-juicer/blob/main/configs/data_juicer_recipes/README.md#before-and-after-refining-for-multimodal-dataset)

## License

Data-Juicer is released under Apache License 2.0.

## Contributing

We are in a rapidly developing field and greatly welcome contributions of new features, bug fixes and better documentations. Please refer to [How-to Guide for Developers](https://github.com/modelscope/data-juicer/blob/main/docs/DeveloperGuide.md).

If you have any questions, please join our [discussion groups](https://github.com/modelscope/data-juicer/blob/main/README.md).

## Acknowledgement

Data-Juicer is used across various LLM products and research initiatives, including industrial LLMs from Alibaba Cloud's Tongyi, such as Dianjin for financial analysis, and Zhiwen for reading assistant, as well as the Alibaba Cloud's platform for AI (PAI). We look forward to more of your experience, suggestions and discussions for collaboration!

Data-Juicer thanks and refers to several community projects, such as [Huggingface-Datasets](https://github.com/huggingface/datasets), [Bloom](https://huggingface.co/bigscience/bloom), [RedPajama](https://github.com/togethercomputer/RedPajama-Data/tree/rp_v1), [Pile](https://huggingface.co/datasets/EleutherAI/pile), [Alpaca-Cot](https://huggingface.co/datasets/QingyiSi/Alpaca-CoT), [Megatron-LM](https://github.com/NVIDIA/Megatron-LM), [DeepSpeed](https://www.deepspeed.ai/), [Arrow](https://github.com/apache/arrow), [Ray](https://github.com/ray-project/ray), [Beam](https://github.com/apache/beam), [LM-Harness](https://github.com/EleutherAI/lm-evaluation-harness), [HELM](https://github.com/stanford-crfm/helm), ....

## References

If you find our work useful for your research or development, please kindly cite the following [paper](https://arxiv.org/abs/2309.02033).

```
@inproceedings{chen2024datajuicer,
title={Data-Juicer: A One-Stop Data Processing System for Large Language Models},
author={Daoyuan Chen and Yilun Huang and Zhijian Ma and Hesen Chen and Xuchen Pan and Ce Ge and Dawei Gao and Yuexiang Xie and Zhaoyang Liu and Jinyang Gao and Yaliang Li and Bolin Ding and Jingren Zhou},
  booktitle={International Conference on Management of Data},
  year={2024}
}
```
