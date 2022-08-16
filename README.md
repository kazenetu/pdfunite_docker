# PDF結合ツール「pdfunite」用dockerfile
複数のPDFファイルを一つにまとめるツール「pdfunite」を  
手軽に利用できるようにdockerfileにまとめた。

## ツールの使い方
* 前提  
  * Docker EngineやDocker Desktopがインストール済みであること。
  * docker-composeがインストール済みであること。

* 実行手順  
  pdfuniteコンテナを起動する。
  1. docker_devに移動  
      ```sh
      cd docker_dev
      ```

  1. (**初回のみ**)ビルド  
      ```sh
      docker-compose build
      ```

  1. コンテナ起動  
      ```sh
      docker-compose up -d
      ```

  1. コンテナに入る。  
      ```sh
      docker exec -it docker_dev_pdfunite_1 /bin/bash
      ```

  1. コンテナ内で実行  
      ※ルートフォルダが「コンテナ上のsourceディレクトリ」となる。
      1. PDF結合を実施する。  
          ```sh
          --例：pdfディレクトリ内のすべてのPDFファイルを結合した結果としてoutput.pdfを作成する
          pdfunite pdf/**/*.pdf output.pdf
          ```

      1. コンテナから離脱する。  
          ```sh
          exit
          ```

  1. コンテナ停止・削除  
      ```sh
      docker-compose down
      ```