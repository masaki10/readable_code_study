## リーダブルコード メモ

どこからページを取得するのか？
```
x def GetPage(url):

o def DownloadPage(url):

o def FetchPage(url):
```

何のsize？

ツリーの高さ？ノードの数？ツリーのメモリ消費量？

Height() NumNodes () MemoryBytes()
```
class BinaryTree {
    ins Size();
};
```

より明確な単語を選ぶ

取り消しができない重い動作 → Kill()

あとからResume()できる → Pause()
```
class Tread {
    void Stop();
};
```

tmpを使っても良い例

生存期間がわずかで、一時的な保管以外に役割がない変数
```
if (right < left) {
    tmp = right;
    right = left;
    left = tmp;
}
```

ループイテレータ（特に多重ループで有効）
```
for (int i = 0; i < clubs.length; i++) {
    for (int j = 0; j < clubs[i].members.length; j++) {
        for (int k = 0; k < users.length; k++) {
            if (clubs[i].members.[j] == users[k]) {
                ...
            }
        }
    }
}

better
if (clubs[clubs_i].members.[members_i] == users[users_i])
if (clubs[ci].members.[mi] == users[ui])
```

名前に情報を追加する
```
id -> hex_id

elapsed -> elapsed_ms
size -> size_mb
limit -> max_kbps

password -> plaintext_password
```

スコープが小さいなら1~2文字でもいい
```
if (debug) {
    map<string,int> m;
    LookUpNamesNumbers(&m);
    Print(m);
}
```

共通で理解できない省略はNG
```
x BackEndManager -> BEManager

o evaluation -> eval
o document -> doc
o string -> str
```

不要な単語を捨てる
```
ConvertToString() -> ToString()
```

エンティティごとにフォーマットを変える
```
static const int kMaxOpenFiles = 100

class LogReader {
    public:
        void openFile(string local_file);
    
    private:
        int offset_;
}


<div id="middle_column" class="main-content"></div>
```

曖昧な言葉を避ける
```
x results = Database.all_objects.filter("year <= 2011")

o results = Database.all_objects.select("year <= 2011")
o results = Database.all_objects.exclude("year <= 2011")
```

限界値を含めるときはmin, maxを使う
```
x CART_TOO_BIG_LIMIT

o MAX_ITEMS_IN_CART
```

範囲を以下で指定するとき
```
integer_range(first=2, last=4) // 2, 3, 4
```

範囲を未満で指定するとき
```
integer_range(begin=2, end=4) // 2, 3
```

get()やsize()などは軽い処理が期待される（ユーザーの期待に合わせる）
```
x getMean() { // 重い処理 }

o computeMean() { // 重い処理 }
```

コードは一貫性のある見た目にする（適切な改行）
```
public class PerformanceTester {
    // TcpConnectionSimulator(throughput, latency, jitter, packet_loss)
    //                           [kbps]     [ms]    [ms]    [percent]

    public static final TcpConnectionSimulator wifi = 
        new TcpConnectionSimulator(500  ,  80, 200, 1);

    public static final TcpConnectionSimulator t3_fiber = 
        new TcpConnectionSimulator(45000,  10,   0, 0);
    
    public static final TcpConnectionSimulator cell = 
        new TcpConnectionSimulator(100  , 400, 250, 5);
}
```

縦の線をまっすぐにする
```
details  = request.POST.get("details")
location = request.POST.get("location")
phone    = request.POST.get("phone")
email    = request.POST.get("email")
url      = request.POST.get("url")
```

一貫性と意味のある並びにする

- 対応するHTMLフォームの<input>フィールドと同じ並びにする
- 「最重要」なものから重要度順に並べる
- アルファベット順に並べる

グループごとに分ける
```
class FrontedServer {
    public:
        FrontedServer();
        ~FrontedServer();

    // ハンドラ
    void ViewProfile(HttpRequest* request);
    void SaveProfile(HttpRequest* request);
    void findFriends(HttpRequest* request);

    // リクエストとリプライのユーティリティ
    string ExtractQueryParam(HttpRequest* request, string param);
    void ReplyOk(HttpRequest* request, string html);
    void ReplyNotFound(HttpRequest* request, string error);
    
    // データベースのヘルパー
    void OpenDatabase(string location, string user);
    void CloseDatabase(string location);
}
```

コードを「段落」に分割する
```
def suggest_new_friends(user, email_password):
    # ユーザの友達のメールアドレスを取得する
    ......

    # ユーザのメールアカウントから全てのメールアドレスをインポートする
    ......

    # まだ友達になっていないユーザーを探す
    ......

    # それをページに表示する
    ......
```

