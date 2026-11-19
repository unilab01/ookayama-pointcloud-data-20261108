# Ookayama Point Cloud Data (2026-11-08 run, rebuilt 2026-11-19)

[Ookayama Point Cloud Viewer](https://unilab01.github.io/ookayama-pointcloud-viewer/colormap/) が読み込む点群データです（GitHub Pages で配信）。

- `v2_5cm/`: Potree 2.0 形式（BROTLI）。5 cm ボクセルの地図のうち、色の付いた 8237 万点。
  2026-11-19 に v1（4 cm 平均、1.27 億点）から差し替えた。v1 は git の履歴に残っている。
  `octree.bin` は GitHub の 1 ファイル 100 MB 制限のため `octree_000.zip`… に分割し、`metadata.json` の `octreeParts` に各ファイルの開始バイトを記録しています。拡張子 `.zip` は、GitHub Pages が `.bin` を gzip で配って Range 読み込みが壊れるのを避けるためで、中身は Potree 2.0 のままです（`hierarchy.zip` も同じ）。
- 作り方: 現行 SLAM 設定（FAST-LIO, LiDAR 3 台, 高さ補正, OctoMap で動く物を除去）で作り直した全点地図を、LIO-SAM のループ閉じ込みで XY とヨーだけ補正し（再訪の二重面を解消）、5 cm ボクセルにまとめ、カメラ画像から面の色を付け（サーフェル）、PotreeConverter 2.1.1 で変換。
