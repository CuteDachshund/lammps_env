# これはなに

Windows10でlammpsを動かすために作成したdocker環境

このディレクトリにいて、

```
docker-compose build
```

して、そのあと
```
docker-compose up -d
```
して、
```
docker-compose exec lammps bash
```
とすればコンテナの中に入れる。

使い終わったら、

```
docker-compose down
```
でコンテナネットワークごと消せる。

## メンテナンス情報

Dockerfileでlammpsのgithubリポジトリからひっぱってきてるから、URLが変わったら多分動かない。

イメージの段階でmake mpiしてパスも通してある。

このディレクトリにあるvolumeとコンテナ内の```/volume```が同期されてるから、
そとからいじりたいやつはこの中で作業するとよい。

## lammpsにパッケージを追加する方法

lammpsには標準gitリポジトリに含まれてはいるが、明示して`build`しないと有効化されない機能(パッケージ)がある。
これを有効化する方法を説明する。
パッケージを有効化するためにはlammpsをソースコードからビルドするときにオプションをつければ良い。
このビルドをするのにmakeをつかうのかcmakeをつかうのか二つの流派がある。
とりあえず簡単そうなmakeをつかう方法を説明してみる。

makeを使ってlammpsにパッケージをいれてみよう。
いま、lammpsのリポジトリに最初から入っているMNYBODYなるパッケージを導入することを考える。
git hubからlammpsのリポジトリを落としてきて、lammpsディレクトリの中のsrcディレクトリに入る。
何もパッケージをいれずにビルドするときは

```
make mpi
```

すると良い。
並列計算をよしなにしてくれるビルドが走る。
いま有効化されているパッケージを確認したいときは、

```
make package-status
```

すると現状が把握できる。

MANYBODYパッケージをいれたいときは、

```
$ make yes-MANYBODY
$ make mpi
```

すれば良い。











