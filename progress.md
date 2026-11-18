# 專案進度（2026-11-18）

> **本專案已停止開發並封存（Archived）。** repo 保留為唯讀，供日後參考；以下待辦不再處理。

## 封存原因

原訂的 local-first 小模型 10 秒延遲門檻（[#94](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/94)）、生成決定性（[#92](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/92)）與長證據生成品質（[#87](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/87)）經評估後決定不再投入調整，改為保留既有成果供日後參考。三個 issue 以「因專案封存而關閉」結案，不代表已解決。

## 已完成成果

- 固定來源抓取與索引：HoYoLAB、Fandom、genshin-db 以 pinned 指標重建，14 文件、89 切塊，`dataset_version f49336564cad6162` 可重現。
- Grounding 守門：證據不足即拒答；未出現在證據的名稱、與證據矛盾的元素會退回附引用的模板。
- 74 題評估基準（64 可答、10 必拒）：Recall@5、正確拒答率、引用率皆 100%；答案正確性與 groundedness 為 `not_scored`。
- 離線單元測試：2026-11-18 在 `main` 以 Node 24 執行 `npm test`，463 tests 全數通過；這不是目標模型驗收。

## 封存時未達成的驗收

| Issue | 封存時狀態 |
|---|---|
| [#87](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/87) 長證據生成品質 | 守門擋住編造，但長篇版本總覽常退回模板；未在目標裝置驗證。 |
| [#92](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/92) 生成決定性 | 評估工具已能連跑三次比對，未實測；先前量測版本總覽散文仍會變動。 |
| [#94](https://github.com/frobel0520/Genshin-Impact-RAG-Helper/issues/94) 10 秒效能門檻 | 實測 44–111 秒，**未通過**；串流驗收與日誌遮罩規則未決議。 |

## 若日後重啟

先讀 `README.md` 重建來源與索引，再從上表三項擇一重新評估；需改用其他模型或架構時，依 Harbor 開發規範記錄 Change Request，並維持零月費限制。
