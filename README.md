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

## Contribution

### Naming Rule

#### Package Name

```
kebab-case
```

### Tips

`*.exe` , `*.msi` 等の拡張子のファイルでも `7zip` で解凍できるファイルは慣用的に `dl.7z` と言う名前にしているよう。
インストールのコードによると、 `*.zip` , `*.exe` 以外はすべて `7zip` で解凍することになっているようだ。
[source code](https://github.com/lukesampson/scoop/blob/ad01bff66750a3a611c0cb0e0af0e5730912a342/lib/install.ps1#L548-L554)

`manifest.json` で以下のように suffix として `#dl.7z` とすれば自動的に解凍される。

```json
{
    "url": "https://example.com/xxx.zip#dl.7z"
}
```
