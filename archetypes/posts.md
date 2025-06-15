---
date: {{ .Date }}
draft: false
title: {{ replace .File.ContentBaseName "-" " " | title }}
type: "post"
layout: default
comments: true
---