# Layihə: iş mühiti

Bu repo Claude Code ilə işləmək üçün ümumi iş mühitidir və yeni layihələr üçün şablon rolunu oynayır. Konkret layihəyə bağlı deyil.

## Budaqlar

- `master` — mühit burada inkişaf etdirilir. Müzakirə sənədləri, vəziyyət və yaddaş mühitin özünə aiddir.
- `template` — yeni layihələrin başlanğıcıdır və GitHub-da default budaqdır. Mühitin qərarları burada yoxdur; layihə sənədləri və yaddaş boş skeletlərdir.

## Yeni layihə yaratmaq

GitHub-da "Use this template" və ya:

```
gh repo create <ad> --template CRazY4485/environment --private --clone
```

Sonra yeni layihədə `.claude/settings.local.json` faylı yaradılır və `autoMemoryDirectory` layihənin `.claude/memory` qovluğunun mütləq yoluna təyin edilir.

## Şablonu yeniləmək

Mühit yalnız `master`-də dəyişdirilir. Sonra ümumi fayllar `template`-ə köçürülür:

```
git switch template
git checkout master -- CLAUDE.md .claude/skills .claude/templates .gitignore .worktreeinclude
git commit -m "Şablonu master ilə yenilə"
git push origin template
git switch master
```

- `docs/decisions/`, `docs/project/`, `.claude/discussions/` və `.claude/memory/` köçürülmür: onlar mühitin özünə aiddir, şablonda isə boş skeletlər var.
- `master`-də silinmiş ümumi faylı `template`-dən `git rm` ilə ayrıca silmək lazımdır.
