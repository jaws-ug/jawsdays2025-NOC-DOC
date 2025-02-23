# jawsdays2025-NOC-DOC
イベント会場でWi-Fiを提供するNOCをやるに当たって必要そうなことをまとめてみました。

## 準備すること一覧
- [jawsdays2025-NOC-DOC](#jawsdays2025-noc-doc)
  - [準備すること一覧](#準備すること一覧)
    - [1. はじめに](#1-はじめに)
      - [ドキュメントの目的と構成](#ドキュメントの目的と構成)
      - [NOCの目的と概要](#nocの目的と概要)
      - [関係者と連絡先](#関係者と連絡先)
    - [2. 事前準備](#2-事前準備)
      - [2.1 回線手配](#21-回線手配)
        - [回線選定と契約](#回線選定と契約)
        - [回線敷設と開通確認](#回線敷設と開通確認)
      - [2.2 機材調達](#22-機材調達)
        - [機材リストと仕様](#機材リストと仕様)
        - [調達手順と保管](#調達手順と保管)
        - [予備機材と保守](#予備機材と保守)
      - [2.3 事務準備](#23-事務準備)
        - [スタッフ体制と役割分担](#スタッフ体制と役割分担)
        - [許可申請と連絡体制](#許可申請と連絡体制)
        - [来場者への情報提供](#来場者への情報提供)
      - [2.4 予算見積もり](#24-予算見積もり)
        - [予算計画と費目](#予算計画と費目)
        - [支出管理と会計処理](#支出管理と会計処理)
    - [3. 物理設計](#3-物理設計)
      - [3.1 電源設計](#31-電源設計)
        - [電源容量と配置](#電源容量と配置)
        - [冗長化と配線](#冗長化と配線)
      - [3.2 AP設置場所](#32-ap設置場所)
        - [会場レイアウトと電波計画](#会場レイアウトと電波計画)
        - [AP配置とLANポート](#ap配置とlanポート)
      - [3.3 ケーブリング計画](#33-ケーブリング計画)
        - [ケーブル種類と敷設ルート](#ケーブル種類と敷設ルート)
        - [配線図と管理](#配線図と管理)
    - [4. 論理設計](#4-論理設計)
      - [4.1 ネットワーク設計](#41-ネットワーク設計)
        - [ネットワーク構成図](#ネットワーク構成図)
        - [ルーティングとVLAN](#ルーティングとvlan)
        - [DHCPとDNS](#dhcpとdns)
        - [ファイアウォールとセキュリティ](#ファイアウォールとセキュリティ)
      - [4.2 サーバー設計](#42-サーバー設計)
        - [サーバ基盤](#サーバ基盤)
        - [DHCP](#dhcp)
        - [DNS](#dns)
        - [なんかのサーバ](#なんかのサーバ)
      - [4.3 WiFi設計](#43-wifi設計)
    - [5. 運用設計](#5-運用設計)
      - [5.1 監視設計](#51-監視設計)
        - [監視項目とツール](#監視項目とツール)
        - [アラートとログ分析](#アラートとログ分析)
      - [5.2 トラブルサポート設計](#52-トラブルサポート設計)
        - [対応フローと報告](#対応フローと報告)
        - [原因究明と再発防止](#原因究明と再発防止)
      - [5.3 ガイドライン作成](#53-ガイドライン作成)
        - [利用規約とセキュリティ](#利用規約とセキュリティ)
        - [利用方法とサポート](#利用方法とサポート)
    - [6. 構築](#6-構築)
      - [6.1 ネットワーク構築](#61-ネットワーク構築)
        - [コアネットワーク](#コアネットワーク)
        - [VLAN、STP、QoS](#vlanstpqos)
        - [セキュリティと管理](#セキュリティと管理)
      - [6.2 サーバ構築](#62-サーバ構築)
        - [サーバ基盤](#サーバ基盤-1)
        - [DHCP](#dhcp-1)
        - [DNS](#dns-1)
        - [なんかのサーバ](#なんかのサーバ-1)
      - [6.3 WiFi構築](#63-wifi構築)
        - [SSID、周波数、ローミング](#ssid周波数ローミング)
        - [ゲストネットワーク](#ゲストネットワーク)
      - [7. NOC設営](#7-noc設営)
        - [設営スケジュールとチェックリスト](#設営スケジュールとチェックリスト)
        - [機材搬入/搬出と点検](#機材搬入搬出と点検)
      - [7.1 電源作業](#71-電源作業)
      - [7.2 ケーブリング作業](#72-ケーブリング作業)
        - [敷設手順と確認](#敷設手順と確認)
        - [ラベリングと整理](#ラベリングと整理)
    - [8. 撤去・撤収](#8-撤去撤収)
      - [8.1 機材撤去](#81-機材撤去)
      - [8.2 ケーブル撤去](#82-ケーブル撤去)
      - [8.3 機材返却](#83-機材返却)
      - [8.4 各種契約の解約](#84-各種契約の解約)
    - [9. その他](#9-その他)
      - [9.1 トラブルシューティング](#91-トラブルシューティング)
        - [よくあるトラブルと解決策](#よくあるトラブルと解決策)
        - [切り分け手順とツール](#切り分け手順とツール)
      - [9.2 ドキュメント/設定類の管理](#92-ドキュメント設定類の管理)
        - [バージョン管理とアクセス権](#バージョン管理とアクセス権)
      - [9.3 バックアップ](#93-バックアップ)
        - [バックアップ](#バックアップ)


### 1. はじめに

#### ドキュメントの目的と構成
各種イベントでWi-Fiを提供するためのノウハウをある程度まとめておいて、いろんなイベントで使い回せるようにするためのドキュメントです。

#### NOCの目的と概要

各種イベントでWiFi提供を行う為にNOC (Network Operation Center) と呼ばれているチームを設けています。
NOCの役割はイベント毎に異なりますが、本書では「各種イベントにボランティアとしてWi-Fiを提供する」事を役割としています。

#### 関係者と連絡先

### 2. 事前準備

各種イベントでWiFiを提供するにあたり事前に準備・考慮しておかなければいけない項目を記載します

#### 2.1 回線手配

##### 回線選定と契約

##### 回線敷設と開通確認

#### 2.2 機材調達

##### 機材リストと仕様
##### 調達手順と保管
##### 予備機材と保守

#### 2.3 事務準備

##### スタッフ体制と役割分担
##### 許可申請と連絡体制
##### 来場者への情報提供

#### 2.4 予算見積もり

##### 予算計画と費目
##### 支出管理と会計処理

### 3. 物理設計

#### 3.1 電源設計

##### 電源容量と配置
##### 冗長化と配線

#### 3.2 AP設置場所

##### 会場レイアウトと電波計画
##### AP配置とLANポート

#### 3.3 ケーブリング計画

##### ケーブル種類と敷設ルート
##### 配線図と管理

### 4. 論理設計

#### 4.1 ネットワーク設計

##### ネットワーク構成図
##### ルーティングとVLAN
##### DHCPとDNS
##### ファイアウォールとセキュリティ

#### 4.2 サーバー設計

##### サーバ基盤

##### DHCP

##### DNS

##### なんかのサーバ

#### 4.3 WiFi設計

### 5. 運用設計

#### 5.1 監視設計

##### 監視項目とツール
##### アラートとログ分析

#### 5.2 トラブルサポート設計

##### 対応フローと報告
##### 原因究明と再発防止

#### 5.3 ガイドライン作成

##### 利用規約とセキュリティ
##### 利用方法とサポート

### 6. 構築

#### 6.1 ネットワーク構築

##### コアネットワーク

##### VLAN、STP、QoS
##### セキュリティと管理

#### 6.2 サーバ構築

##### サーバ基盤

##### DHCP

##### DNS

##### なんかのサーバ

#### 6.3 WiFi構築

##### SSID、周波数、ローミング
##### ゲストネットワーク

#### 7. NOC設営

##### 設営スケジュールとチェックリスト

##### 機材搬入/搬出と点検

#### 7.1 電源作業

#### 7.2 ケーブリング作業

##### 敷設手順と確認
##### ラベリングと整理

### 8. 撤去・撤収

#### 8.1 機材撤去

#### 8.2 ケーブル撤去

#### 8.3 機材返却

#### 8.4 各種契約の解約



### 9. その他

#### 9.1 トラブルシューティング

##### よくあるトラブルと解決策
##### 切り分け手順とツール

#### 9.2 ドキュメント/設定類の管理

##### バージョン管理とアクセス権

#### 9.3 バックアップ

##### バックアップ
