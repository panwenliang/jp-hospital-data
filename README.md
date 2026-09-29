# jp-hospital-data

Per-prefecture hospital / clinic / dental and pharmacy files for [jp-hospital-finder](https://github.com/panwenliang/jp-hospital-finder).

Snapshot: **20260601**. Foreign-patient list date: **2026-08-06**.

## Layout

| Path | Content |
|---|---|
| `manifest.json` | Version, checksums, sizes, and record counts |
| `facilities/meta.json.gz` | Shared department dictionary and national totals |
| `facilities/NN.json.gz` | Compact Navii facilities for prefecture `NN` |
| `pharmacies/NN.json.gz` | Pharmacies for prefecture `NN` |

CDN URLs used by the app:

- `https://cdn.jsdelivr.net/gh/panwenliang/jp-hospital-data@main/<path>`
- fallback `https://raw.githubusercontent.com/panwenliang/jp-hospital-data/main/<path>`

## Attribution (PDL 1.0)

Both MHLW sources are published under **公共データ利用規約（第1.0版）(PDL1.0)**. Because the data is processed, the credit must say so, and must not imply the government made or endorses the app.

```
出典：厚生労働省「外国人患者を受け入れる医療機関の情報を取りまとめたリスト」
（https://www.mhlw.go.jp/content/10800000/001733200.xlsx）、
厚生労働省「医療情報ネット（ナビイ）」オープンデータ
（https://www.mhlw.go.jp/stf/seisakunitsuite/bunya/kenkou_iryou/iryou/newpage_43373.html）
（公共データ利用規約 第1.0版 https://www.digital.go.jp/resources/open_data/public_data_license_v1.0）を加工して作成
一部の位置情報は国土地理院の住所検索APIを利用して取得
本アプリは厚生労働省が作成・提供するものではありません。
```

English: Source: Ministry of Health, Labour and Welfare (MHLW), "List of medical institutions accepting foreign patients" and "Iryō Jōhō Net (Navii)" open data, processed under the Public Data License v1.0. Some locations geocoded with the GSI address search. Not an official MHLW service.

中文：数据来源：日本厚生劳动省『接收外国患者的医疗机构名单』及『医疗信息网（Navii）』开放数据，经加工（公共数据利用规约 PDL1.0）。部分位置由国土地理院地址检索获得。并非厚生劳动省官方服务。

## Regenerate

From the finder repo (government sources under `tools/data-pipeline/src/`, not in git):

```bash
cd tools/data-pipeline
./run_all.sh src/mhlw_001733200.xlsx 20260601 2026-08-06
./pack_data_repo.sh
```

That writes this tree (or `tools/data-repo/` when packaging from the finder repo). Copy or push the result to this repository's `main`.
