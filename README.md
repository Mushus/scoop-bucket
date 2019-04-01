# scoop-bucket
scoop bucket

## How to Use

### Install scoop

See [lukesampson/scoop](https://github.com/lukesampson/scoop).

### Add bucket

```
scoop bucket add mushus git@github.com:Mushus/scoop-bucket.git
```

### Install apps

```
scoop update
scoop install [app]
```

VST Path:
```
%USERPLOFILE%\.vst
```

## Apps (VST)

### A

* Ample Bass P Lite II ( [ample-bass-p-lite](bucket/ample-bass-p-lite.json) )
* Ample Guiter M Lite II ( [ample-guiter-m-lite](bucket/ample-guiter-m-lite.json) )

### B

* Bit Box ( [bit-box](bucket/bit-box.json) )

### D

* Drum Pro ( [drum-pro](bucket/drum-pro.json) )

### K

* Kairatune ( [kairatune](bucket/kairatune.json) )

### M

* MEDUSA ( [medusa](bucket/medusa.json) )
* MT Power DrumKit ( [mt-power-drum-kit](bucket/mt-power-drum-kit.json) )

### P

* PianoOne ( [piano-one](bucket/piano-one.json) )

### S

* SANA8BitVST ( [sana-8bit-vst](bucket/sana-8bit-vst.json) )
* sforzando ( [sforzando](bucket/sforzando.json) )
* Synth1 ( [Synth1](bucket/synth1.json) )

### T

* TAL-Elek7ro ( [tal-elek7ro](bucket/tal-elek7ro.json) )

## Contribution

### Naming Rule

#### Package Name

```
kebab-case
```

### Tips

#### exe ファイルの簡易展開

`*.exe` , `*.msi` 等の拡張子のファイルでも `7zip` で解凍できるファイルは慣用的に `dl.7z` と言う名前にしているよう。  
インストールのコードによると、 `*.zip` , `*.msi` 以外はすべて `7zip` で解凍することになっているようだ。  
[source code](https://github.com/lukesampson/scoop/blob/ad01bff66750a3a611c0cb0e0af0e5730912a342/lib/install.ps1#L548-L554)

`manifest.json` で以下のように suffix として `#dl.7z` とすれば自動的に解凍される。

```json
{
    "url": "https://example.com/xxx.exe#dl.7z"
}
```

#### アンインストーラーによるアンインストール

アンインストールを `scripts` で記述する場合、 exe ファイルの実行を待ってくれない。  
その状態でアンインストーラーを実行するとディレクトリが速やかに削除され、アンインストーラーが失敗することがある。  
exe ファイルが終了するまで待機する必要があるが、以下の記述で可能。  

```json
{
    "uninstaller": {
        "scripts": [
            ". $dir\\unins000.exe /VERYSILENT /SUPPRESSMSGBOXES | Out-Null"
        ]
    }
}
```

#### サイレントインストール方法を調べる

`/?` フラグをつけると教えてくれることもある。

```
. .\dl.exe /?
```
