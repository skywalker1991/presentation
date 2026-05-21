# Superpowers Skills 紹介

## 1. Skillとは何か

操作規範を書いたMarkdownファイル。Agentがタスク前に自動判断して読み込み、従う。

```mermaid
flowchart LR
    A["依頼"] --> B["Skillを自動判断"]
    B --> C["SKILL.mdを読む"]
    C --> D["規範通りに実行"]
```

## 2. Superpowersとは何か

AIの「能力」ではなく「行動」を制御するSkillのコレクション。Promptで毎回伝えなくても、Claudeが自律的に遵守する。

```mermaid
flowchart LR
    P["Prompt\n毎回指示が必要\n従うかはAI次第"]
    S["Superpowers\nSkillとして固化\n自動で遵守"]
    P -.-> S
```

**主なSkill：**

| Skill | 内容 |
|---|---|
| brainstorming | 要件を明確化し、specとして保存 |
| writing-plans | specをタスクに分解 |
| subagent-driven-development | タスクごとにagentを分離 |
| test-driven-development | テストなしのコードは削除してやり直し |

## 3. 私の使い方

```mermaid
flowchart TD
    R["資料調査・認知構築"]
    R --> H

    subgraph H ["高レベル設計"]
        H1["brainstorming"] --> H2["概念spec"]
    end

    H --> T

    subgraph T ["各ステップで繰り返す（技術選定・データモデル・API設計…）"]
        L1["brainstorming"] --> L2["spec保存"] --> L3["writing-plans"] --> L4["実行"]
    end

    T -. "問題発見時\n前のドキュメントに戻る" .-> H
    T -. "問題発見時\n同じステップを更新" .-> T
```

コンテキストはファイルに残る。セッションが終わっても、人が変わっても続きから始められる。