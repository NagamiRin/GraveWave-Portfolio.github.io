<link rel="stylesheet" href="style.css">

# <font color="#ffffffff">「Grave Wave」　ポートフォリオ</font>


<img src="Title.png" width="1000">

<br>
<br>

ゲームPVは[こちら](https://www.youtube.com/watch?v=Y3ZdnPw-Aho)！！！<br>

<br>
<br>

## <font color="#ff0000">目次</font>

---



<ul>
  <li><a href="#概要紹介">概要紹介</a>
    <ul>
      <li><a href="#作品概要">作品概要</a></li>
      <li><a href="#開発環境">開発環境</a></li>
    </ul>
  </li>
  
  <li><a href="#ゲーム内容紹介">ゲーム内容紹介</a></li>
        <li><a href="#ゲームの流れ">ゲームの流れ</a></li>
        <li><a href="#このゲームのポイント">このゲームのポイント</a></li>

  
  <li><a href="#技術紹介">技術紹介</a>
    <ul>
      <li><a href="#疎結合化">疎結合化</a></li>
      <li><a href="#オブジェクトプール">オブジェクトプール</a></li>
      <li><a href="#LOD">LOD</a></li>
      <li><a href="#衝突判定">衝突判定</a></li>
      <li><a href="#データ駆動設計">データ駆動設計</a></li>
      <li><a href="#その他の技術紹介">その他の技術紹介</a>
        <ul>
           <li><a href="#フォグ">フォグ</a></li>
           <li><a href="#マルチスレッドの試み">マルチスレッドの試み</a></li>
           <li><a href="#ステートパターン">ステートパターン</a></li>
           <li><a href="#シングルトンパターン">シングルトンパターン</a></li>
        </ul>
      </li>
    </ul>
  </li>
  
  <li><a href="#今後の展望">今後の展望</a></li>
</ul>
<br>
<br>



<h2 id = "概要紹介" style="color: red;">概要紹介</h2>

---

<h3 id = "作品概要" style="color: red;">作品概要</h3>

---

- <font color="#ffff00">ゲームタイトル</font>
　　　　　　Grave Wave

- <font color="#ffff00">ゲームジャンル</font>
　　　　　　FPSタワーディフェンス

- <font color="#ffff00">プレイ人数</font>
　　　　　　　1人

- <font color="#ffff00">開発期間</font>
　　　　　　　5か月

<br>


<h3 id = "開発環境" style="color: red;">開発環境</h3>

---

- <font color="#ffff00">使用言語</font>
　　　　　　　C++（C++14）

- <font color="#ffff00">使用エンジン</font>
　　　　　　学内エンジン（DirectX12）

- <font color="#ffff00">プラットフォーム</font>
　　　　　 Windows11

- <font color="#ffff00">使用ツール</font>
　　　　　　　Visual Studio 2022,GitHub

<br>
<br>


<h2 id = "ゲーム内容紹介" style="color: red;">ゲーム内容紹介</h2>

---



<h3 id = "ゲームの流れ" style="color: red;">ゲームの流れ</h3>

---

<img src="ゲーム紹介01.png" width="500">

荒野の奥から大量のゾンビが迫ってくる！！
<br>
<br>


<img src="ゲーム紹介02.png" width="500">

銃でゾンビを撃退して防壁を守る！！
<br>
<br>


<img src="ゲーム紹介03.png" width="500">

最終ウェーブのボスを撃破すると、ゲームクリア！！！
<br>
<br>


<h3 id = "このゲームのポイント" style="color: red;">このゲームのポイント</h3>

---

このゲームの肝は、「<font color="#ffff00">どれだけ速やかにゾンビを撃退できるか</font>」

プレイヤーには射撃精度と視野の広さが問われ、<br>
ゾンビを正確に撃ち抜き、迅速に殲滅していくと同時に、<br>
常に周りをみて、防壁に接近しているゾンビがいないかを注視していく必要がある。

<br>
<br>


<h3 id = "ショップ" style="color: red;">ショップ</h3>

---

準備フェーズに銃や弾薬を購入できるシステムを実装。<br>
様々な銃を試すことができ、プレイスタイルの幅を広げることができた。<br><br>
<img src="ショップ.png" width="500">

<br>
<br>
<br>



<h2 id = "技術紹介" style="color: red;">技術紹介</h2>

---


<br>

<h3 id = "疎結合化" style="color: red;">疎結合化</h3>

---

<br>

モジュール間の疎結合化を意識してクラス設計を行った。

<br>

<font color="#ffff00">実装方法</font>


<img src="技術紹介01.png" width="500">

<br>

モジュールが他のモジュールを直接知らなくても実装できるような形で実装進め、
他の管理クラスが必要となる情報だけを教えるなど、「必要最低限のことしか教えない設計」で実装を行った。<br>
１か箇所の変更で他クラスに影響することがなくなり、保守性、拡張性の高い設計にすることができた。

<br>
<br>


<font color="#ffff00">実装の意図</font>

<img src="技術紹介02.png" width="500">

<br>

過去のゲーム制作では、結合度をあまり意識せず、モジュール間の繋がりが強い状態で実装を進めていた。<br>
その結果、一つの変更が他に影響してしまう結果に。デバッグや新規実装が非効率なものとなってしまった。<br>
今回の制作では、長期的な開発効率を意識した実装を行った。
「今だけのコード」ではなく、「後々見返したときに修正、拡張がしやすいか」を始めから意識するように心がけた。

<br>
<br>


<h3 id = "オブジェクトプール" style="color: red;">オブジェクトプール</h3>

---

<br>

ゾンビのスポーンをオブジェクトプールにて行った。

<font color="#ffff00">実装方法</font>

<img src="技術紹介07.png" width="700">

↑オブジェクトプール実装イメージ↑<br><br>

実装の流れは以下の通り

1. インゲームに入る際、そのゲーム中で出現するであろうゾンビの最大数をあらかじめ生成。
2. インゲーム中は生成削除を行わず、プールとフィールドを行き来させる。

<br>

この実装方法では、インゲーム中にゾンビの生成削除を行わない。<br>
そのため、ゲーム中はCPUへの負荷を安定させ、フレームレートを一定に保てるだけでなく、
メモリの断片化を防ぎ、メモリ不足に陥るリスクを抑えることもできた。

<br>

<font color="#ffff00">実装の意図</font>

<img src="技術紹介03-1.gif" width="500">

↑new、deleteの瞬間にメモリ使用量が多くなっている様子（イメージ）↑<br>
<br>


<img src="技術紹介04-1.gif" width="500">

↑メモリの断片化（イメージ）↑<br>
<br>


実装前はゲーム中にゾンビの生成と削除を繰り返していた。<br>
その結果、生成、削除の瞬間だけ、フレームレートが著しく低下し、ユーザー体験を損ねてしまっていた。<br>
また、メモリの断片化が起き、動作環境によってはメモリ不足に陥ってしまう可能性があった。

<br>
<br>
<br>

<h3 id = "LOD" style="color: red;">LOD</h3>

---

<br>

ゾンビの描画処理にLOD処理を加えた。<br>


<font color="#ffff00">実装方法</font>

<img src="技術紹介10.png" width="600">

↑LODの実装イメージ↑
<br>
<br>

実装手順は以下の通り

1. ゾンビのスポーン時はLOWモデルで描画。
2. カメラとゾンビとの距離が一定距離になったら、、、
3. Highモデルに切り替える。<br>

この実装手段を取ることで、インゲーム中のGPUへの負荷を一定に保つことができた。<br>
ユーザーからの見た目を一定に保ちつつ、フレームレートの低下を抑えることができた。<br>

<img src="LOD_before.gif" width="600">

↑LODを実装する前の実行画面の様子↑
<br>
<br>

<img src="LOD_after.gif" width="600">

↑LODを実装した後の実行画面の様子↑
<br>
<br>

<font color="#ffff00">実装の意図</font>
<br>

対策を施さずにゾンビを大量生成すると、GPUへの負荷が高くなってしまった。<br>
その結果、フレームレートの低下が目立つ結果となり、プレイ体験を損ねてしまっていた。<br>
また、動作環境によっては少ない生成数でも負荷がかかってしまうと考えた。

<br>
<br>
<br>

<h3 id = "衝突判定" style="color: red;">衝突判定</h3>

---

<br>

弾丸と目標物との当たり判定をSweepTestを用いて行った。<br>


<font color="#ffff00">実装方法</font>

<img src="Sweep_after.gif" width="600">

↑SweepTestで処理を行い、衝突判定が安定した図（イメージ）↑

<br>

SweepTestの処理手順は以下の通り<br>
（学内エンジンで簡易的に使用できるようにはされている）

1. 弾丸の現在位置（始点）を取得する。
2. 弾丸の次のフレームに移動する位置（終点）を計算する。（移動ベクトル　×　移動速度）
3. 始点から終点までの大きさのコリジョンを置く。（指定した太さで）
4. コリジョンにヒットしたものがある場合trueを返す。

<br>

この手段を取ることで、弾の速さ、大きさに関わらず、衝突判定を取ることができた。


また、SweepTestを用いるにあたって、内部では多くのゲームでも使用されているBulletPhysicsを使用している。<br>
だが、そのままの状態では「衝突判定」はとれるものの、「何に衝突したか」は取得できないものとなっている。<br>
「どの弾が、どのゾンビに衝突したか」という対象物の情報が取れるような改造を施した。

<br>


修正箇所は以下の通り

```cpp
btScalar addSingleResult(btCollisionWorld::LocalConvexResult& convexResult, bool normalInWorldSpace) override
{
    //自分自身を弾く
    if (&m_me->GetbtCollisionObject() == convexResult.m_hitCollisionObject) return 0.0f;
    //エネミー以外かつゴーストオブジェクトではない時
    if (convexResult.m_hitCollisionObject->getUserIndex() != nsApp::enCollirionEnemy
        && convexResult.m_hitCollisionObject->getInternalType() != btCollisionObject::CO_GHOST_OBJECT) {
        return 0.0f;
    }
    isHit = true;
    m_you = convexResult.m_hitCollisionObject;
    return 0.0f;
```

<br>
<br>

<font color="#ffff00">実装の意図</font>

<img src="Sweep_before.gif" width="600">

↑実装前に弾の当たり判定が安定しなかった図（イメージ）↑

<br>

コリジョンだけののシンプルな衝突判定では、フレームごとのコリジョンの位置でしか判定を取ることができない。<br>
そのため、弾の速さ、大きさによっては目標物を飛び越えてしまい、安定した判定を取得できなかった。<br>
弾のステータスに関わらず、安定した判定を取れ、弾の太さも考慮したSweepTestを用いることで、プレイ体験はそのままに、安定した判定を取得できるようになるのではと考えた。

<br>
<br>
<br>


<h3 id = "データ駆動設計" style="color: red;">データ駆動設計</h3>

---

数値調整時のイテレーション速度の向上のため、
「ゾンビのHP」「弾の速さ」といった情報をjsonファイルにて調整できるようにした。

ゲーム起動時に情報を外部から読み込むようにすることで、
数値調整を施しても、ビルドをする必要がなくなった。

```json
"Comment": "ゾンビ用のパラメータ",
"MoveSpeed":0.3,
"HP":10,
"AttackPower":3,
"AttackFrequency":3.0,
"AttackRange":50.0
```
↑ゾンビのステータスを記載したjsonファイル↑


#### <font color="#ffff00">ホットリロード</font>

また、ホットリロードの機能も実装した。<br>
ゲーム実行中でも数値調整を行うことができ、さらにイテレーション速度を向上させることができた。

<img src="ホットリロード.gif" width="600">

↑ホットリロードを使用した数値調整↑




<h3 id = "その他の技術紹介" style="color: red;">その他の技術紹介</h3>

---

<h4 id = "フォグ" style="color: yellow;">フォグ</h4>

ゾンビのスポーンやLODの切り替わりをプレイヤーから見えなくさせるため、
簡易的なフォグを実装した。

<img src="fog.png" width="600">

↑ゲーム実行画面↑

実装方法はシンプルで、カメラとオブジェクトとの距離を測り、
その距離に応じてテクスチャにフォグの色をかける。<br>
という方法で実装した。

<img src="fogImage.png" width="600">

↑フォグ実装イメージ↑

<br>

<h4 id = "マルチスレッドの試み" style="color: yellow;">マルチスレッドの試み</h4>

更なるCPU負荷軽減を図るため、処理のマルチスレッド化を試みた。<br>
実装箇所はエネミーと弾丸の当たり判定をチェックするfor文をマルチスレッドで行うよう試みた。<br><br>

```cpp
for (auto* bulletInfo : bulletInfoList) {
	auto* bullet = dynamic_cast<nsApp::nsActor::nsBullet::NormalBullet*>(bulletInfo->m_object);
	// Sweepテストで衝突判定をする
	Vector3 start = bullet->GetLocalPosition();
	Vector3 end = start + (bullet->GetFlyDirection() * bullet->GetBulletSpeed());
	auto* btCollision = &bulletInfo->m_collision->GetbtCollisionObject();
	auto* collisionShape = btCollision->getCollisionShape();
	BulletCallback cb;
	PhysicsWorld::GetInstance()->ConvexSweepTest(collisionShape, start, end, cb);
	if (cb.isHit) {
		auto* targetInfo = FindBulletCollisionInfo(cb.m_you);
		if (targetInfo) {
			m_collisionPairList.push_back(CollisionPair(bulletInfo, targetInfo));
		}
	}
}
```
↑処理をマルチスレッドにしたfor文↑<br><br>

だが、マルチスレッドにすることによってむしろ処理時間が伸びてしまった。<br>
原因としては、エネミーがマルチスレッドを導入する必要があるほどの数ではなく、<br>
スレッド間のデータの受け渡すコスト方が上回ってしまっていると考えられる。<br><br>

<img src="multisled_before.png" width="300">

↑変更前の処理時間↑<br><br>

<img src="multisled_after.png" width="300">

↑マルチスレッド実装後の処理時間↑<br><br>


今後、エネミーの総数が増えたり、他の箇所で導入する必要があるあった場合は実装したい。


<br>

<h4 id = "ステートパターン" style="color: yellow;">ステートパターン</h4>

エネミーなどのキャラクターの状態ごとの処理を分離し、実装、デバッグをしやすくするため、
ステートパターンで状態遷移、及び状態ごとの処理を行った。

実装することで、状態の処理が分離され、一クラスごとの責任を分散することができた。<br>
状態ごとの処理が干渉しにくくなり、保守性、拡張性が高い実装になった。


```cpp
void StateMachine::Update()
{
    if (m_currentStateId != m_requestStateId)
    {
        IState* nextState = FindState(m_requestStateId);
        K2_ASSERT(nextState, "次の状態が見つからない");
        if (nextState) {
            if (m_currentState) {
                m_currentState->Exit();
            }
            nextState->Enter();
            m_currentState = nextState;
        }
        m_currentStateId = m_requestStateId;
    }
    if (m_currentState) {
        m_currentState->Update();
    }
}
```
↑StateMachineでの、各Stateへの遷移の処理↑<br><br>



```cpp
void ZombieDeathState::Enter()
{
    auto* owner = GetOwner<ZombieStateMachine>()->GetOwner();
    owner->GetModel()->PlayAnimation(Zombie::EnAnimationVar_Death);
}

void ZombieDeathState::Update()
{
    auto* owner = GetOwner<ZombieStateMachine>()->GetOwner();

    //一定時間後にプールに戻す
    m_currentTime += g_gameTime->GetFrameDeltaTime();
    if (m_currentTime >= RESTORE_TIME) owner->SetRestore(true);
}

void ZombieDeathState::Exit()
{
}
```
↑DeathState時の処理↑

<br>

<h4 id = "シングルトンパターン" style="color: yellow;">シングルトンパターン</h4>


管理クラスが複数生成されることによって発生する、不具合の抑制、
及び、管理クラスへのアクセスの簡略化を目的に、<br>
シングルトンパターンを用いて、管理クラスの生成を行った。

管理クラスの唯一性を保つことができ、クラスが複数を生成されてしまうリスクを防ぐだけでなく、<br>
グローバルアクセスになるため、各クラスが管理クラスへとアクセスできなくなる。<br>
（かといって、多くのクラスが管理クラスを知らなくてもいいようなクラス設計をしている）

```cpp
private:
    /** 自身のインスタンス */
    static BattleManager* m_instance;

public:
    /** BattleManagerクラスのインスタンスを作成 */
    static void CreateInstance()
    {
        if (!m_instance) m_instance = new BattleManager();
    }
    /** BattleManagerクラスのインスタンスを削除 */
    static void DeleteInstance()
    {
        if (m_instance) {
            delete m_instance;
            m_instance = nullptr;
        }
    }
    /** BattleManagerクラスのインスタンスを取得 */
    static BattleManager* GetInstance() { return m_instance; }
```
↑管理クラスのヘッダーファイルの一部↑

<br>
<br>


<h2 id = "今後の展望" style="color: red;">今後の展望</h2>

---

#### <font color="#ffff00">さらなるデータ駆動設計</font>

イテレーション速度上げていき、さらなる開発の効率化へ！！<br>
今後は数値だけではなく、「行動パターン」や「オブジェクトの配置」なども調整できるようにしたいと考えている。<br>
（オブジェクト配置は外部GUIツールを用いて視覚的に行えるように）

<br>

#### <font color="#ffff00">メモリアロケーター</font>

今回のオブジェクトプール実装に伴い、メモリ管理を意識するようになった。<br>
だが、すべてのオブジェクトのnewなどでは活用できていない。<br>
今後はメモリアロケーターを自身で作成して、自身でメモリ管理を行い、
メモリへの理解をさらに深めていきたい。

[def]: #概要紹介


<br><br><br>
---
作成者<br>
　　河原電子ビジネス専門学校　ゲームクリエイター科２年<br>
　　永見 凜


メールアドレス<br>
　　ca01244021@st.kawahara.ac.jp


    
