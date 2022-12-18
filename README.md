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

