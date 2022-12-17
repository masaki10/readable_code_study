## リーダブルコード メモ

どこからページを取得するのか？
```
x def GetPage(url):

o def DownloadPage(url):

o def FetchPage(url):
```

何のsize？

ツリーの高さ？ノードの数？ツリーのメモリ消費量？

Height()&nbsp&nbsp&nbsp&nbsp&nbsp&nbspNumNodes()  MemoryBytes()
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