---
title: Sublime Text 3
tags: ["Android", "JAVA"]
notebook: George 的笔记本
---
<!-- MarkdownTOC -->

- [Evernote user](#evernote-user)
- [MarkdownTOC](#markdowntoc)
- [KeyBind](#keybind)

<!-- /MarkdownTOC -->

# Evernote user

```css
{
 "code_highlighting_style": "github",
"inline_css":
{
"blockquote": "border-left: 10px solid #e7ecee; background-color:#f2f4f6; margin-left: 0px; padding-left: 1em; padding:20px; margin-top: 1.4285em; margin-bottom: 1.4285em;",
"body": "font-size:16px; font-family:微軟正黑體; ",
"footnotes": "border-top: 1px solid #9AB39B; font-size: 80%;",
"h1": "margin-bottom: 1em; margin-top: 1.2em; font-size:2.25em; border-bottom:1px solid #eee;",
"h2": "font-size:1.75em; border-bottom:1px solid #eee;",
"h3": "font-size:1.5em",
"h4": "font-size:1.25em",
"h5": "font-size:1em",
"h6": "font-size:1em; color:#777",
"code": "color:#000000; font-family: monospace; font-size: 0.9em;",
"img": "max-width:100%;",
"hr": "color:#9AB39B;background-color:#9AB39B;height:1px;border:none;",
"inline-code": "color: #C7254E; font-family: monospace; padding: 0.1em 0.2em; margin: 0.1em; font-size: 95%; background-color: #F9F2F4; border-radius: 3px; border: 1px solid #f4e1e6;",
"pre": "color: #000000; font-family: monospace,monospace; font-size: 0.9em; white-space: pre-wrap; word-wrap: break-word; border: 1px solid #cccccc; border-radius: 3px; overflow: auto; padding: 6px 10px; margin-bottom: 10px;",
"sup": "color:#6D6D6D;font-size:1ex",
"table": "border-collapse: collapse; border-spacing: 0; margin: 1em;",
"td": "border: 1px solid #DDD; padding: 6px 13px;",
"th": "border: 1px solid #DDD; padding: 6px 13px;",
"tr:even": "border: 1px solid #DDD; padding: 6px 13px; background-color: #F8F8F8;",
"tr:odd": "border: 1px solid #DDD; padding: 6px 13px;"
},
 "noteStoreUrl": "https://app.yinxiang.com/shard/s1/notestore",
 "token": "S=s1:U=55fba:E=15e1c6cc063:C=156c4bb9150:P=1cd:A=en-devtoken:V=2:H=43b88078b390025a0bf9ae553f26f05d"
}
```

# MarkdownTOC 

```css

{
  "default_autolink": true,            #目录以链接形式呈现
  "default_bracket": "round",        #目录以链接形式呈现
  "default_depth": 0                  #无限目录深度
}

```

# KeyBind

```css
[
 { "keys": ["shift+enter"], "command": "run_macro_file", "args": {"file": "Packages/Default/Add Line.sublime-macro"} },
 { "keys": ["alt+up"], "command": "swap_line_up" },
 { "keys": ["alt+down"], "command": "swap_line_down" },
 { "keys": ["ctrl+alt+j"], "command": "join_lines" },
 { "keys": ["ctrl+alt+down"], "command": "duplicate_line" },
 { "keys": ["shift+ctrl+r"], "command": "show_overlay", "args": {"overlay": "goto", "show_files": true} },
 { "keys": ["ctrl+shift+s"], "command": "save_all" },
 { "keys": ["ctrl+l"], "command": "show_overlay", "args": {"overlay": "goto", "text": ":"} },
 { "keys": ["shift+ctrl+f4"], "command": "close_all" },
 { "keys": ["shift+ctrl+y"], "command": "lower_case" },
 { "keys": ["shift+ctrl+x"], "command": "upper_case" },
 { "keys": ["ctrl+d"], "command": "run_macro_file", "args": {"file": "Packages/Default/Delete Line.sublime-macro"} },
 { "keys": ["ctrl+shift+e"], "command": "show_overlay", "args": {"overlay": "command_palette", "text": "Evernote: "} },
 { "keys": ["ctrl+e", "ctrl+s"], "command": "send_to_evernote" },
 { "keys": ["ctrl+e", "ctrl+o"], "command": "open_evernote_note" },
 { "keys": ["ctrl+e", "ctrl+n"], "command": "new_evernote_note" },
 { "keys": ["ctrl+s"], "command": "save_evernote_note", "context": [{"key": "evernote_note"}] },
 { "keys": ["ctrl+s"], "command": "send_to_evernote", "context": [{"key": "evernote_note", "operator": "equal", "operand": false}, {"key": "selector", "operator": "equal", "operand": "text.html.markdown.evernote"}] },
 { "keys": ["alt+m"], "command": "markdown_preview", "args": { "target": "browser"} }
]

```
