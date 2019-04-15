# Pecoでhistory検索を見やすく
## Pecoとは
[peco](https://github.com/peco/peco#mac-os-x--homebrew)は、インクリメンタルサーチができる検索ツール。

今回は`ctr + R`のコマンドのhistory検索の時に使えるようにバインド


## 導入手順
- homebrewでpecoをインストール
- bashrcに以下のような記述を追加する
```bash
peco-history() {
  local NUM=$(history | wc -l)
  local FIRST=$((-1*(NUM-1)))

  if [ $FIRST -eq 0 ] ; then
    # Remove the last entry, "peco-history"
    history -d $((HISTCMD-1))
    echo "No history" >&2
    return
  fi

  local CMD=$(fc -l $FIRST | sort -k 2 -k 1nr | uniq -f 1 | sort -nr | sed -E 's/^[0-9]+[[:blank:]]+//' | peco | head -n 1)

  if [ -n "$CMD" ] ; then
    # Replace the last entry, "peco-history", with $CMD
    history -s $CMD

    if type osascript > /dev/null 2>&1 ; then
      # Send UP keystroke to console
      (osascript -e 'tell application "System Events" to keystroke (ASCII character 30)' &)
    fi

    # Uncomment below to execute it here directly
    # echo $CMD >&2
    # eval $CMD
  else
    # Remove the last entry, "peco-history"
    history -d $((HISTCMD-1))
  fi
}

bind '"\C-r":"peco-history\n"'

```
- `source ~/.bashrc`を叩く
