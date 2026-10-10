---
name: memory-review
description: Layihənin auto memory qovluğunu (.claude/memory) nəzərdən keçirir və steril saxlayır — köhnəlmiş, təkrarlanan, koddan çıxarıla bilən və ya başqa layihəyə aid qeydləri tapır, indeksi qaydaya salır. İstifadəçi yaddaşın yoxlanmasını istəyəndə və ya son baxışdan çox vaxt keçəndə istifadə et.
---

# Yaddaşın nəzərdən keçirilməsi

Məqsəd: yaddaşda yalnız doğru, aktual, bu layihəyə aid və başqa mənbədən əldə edilə bilməyən qeydlər qalsın.

## 1. Mənzərəni topla

- Sistem promptundakı yaddaş yolunun bu repo-nun `.claude/memory/` qovluğu olduğunu yoxla. Belə deyilsə, istifadəçiyə bildir.
- `MEMORY.md` faylını və bütün topic fayllarını oxu.
- Maşın-lokal qovluğa da bax: `~/.claude/projects/<layihə-slug>/memory/`. Yönləndirmədən əvvəl yazılmış qeydlər orada qala bilər; onları da bu baxışa daxil et.
- Son baxışdan bəri nəyin dəyişdiyini görmək üçün `git log -- .claude/memory` kömək edir.

## 2. Hər qeydi qiymətləndir

Hər qeyd üçün bir qərar seç:

- **saxla** — doğrudur, aktualdır, başqa yerdən əldə edilmir.
- **yenilə** — fakt dəyişib, yaxud `modified` tarixi köhnədir və məzmunu yenidən təsdiqləmək lazımdır.
- **birləşdir** — eyni mövzuda bir neçə qeyd var.
- **docs/-a köçür** — qeyd layihə biliyidir (vəziyyət, qərar, layihənin təsviri). Yaddaşda yalnız `user`, `feedback` və `reference` tipli qeydlər qalır.
- **sil** — koddan və ya git-dən çıxarıla bilir, yanlışdır, aid olduğu iş bitib, başqa layihəyə aiddir, yaxud CLAUDE.md və ya `docs/` ilə təkrarlanır və ya onlara ziddir.

Qeydi yoxlamadan "köhnəlib" demə: adı çəkilən faylları, funksiyaları və əmrləri kodda axtar, lazım olsa `git log`-a bax.

## 3. İndeksi qaydaya sal

- Hər topic faylının `MEMORY.md`-də bir sətri olmalı, hər sətir də mövcud fayla işarə etməlidir.
- `MEMORY.md` 200 sətir / 25KB yükləmə limitindən xeyli aşağı qalmalıdır (təxminən 150 sətir). Limitdən sonrakı hissə sessiyaya yüklənmir.
- Hədəfi silinmiş `[[ad]]` keçidlərini düzəlt.

## 4. Təsdiq al və tətbiq et

- Planı istifadəçiyə qısa cədvəl kimi göstər: qeyd → qərar → səbəb. Silmə və `docs/`-a köçürmə üçün açıq təsdiq al. İndeks düzəlişləri kimi mexaniki işləri birbaşa et.
- Dəyişikliklər `git diff` ilə görünür və geri qaytarıla bilər. Maşın-lokal qovluqdakı fayllar git-də deyil; onları silməzdən əvvəl surətini scratchpad-ə çıxar.
- Sonda `MEMORY.md`-nin ilk sətrindəki tarixi bugünkü tarixlə yenilə: `Son baxış: YYYY-MM-DD`.
- Uyğun olarsa, `CLAUDE.md` üçün də `/doctor prompt-audit` təklif et — o, təlimat fayllarındakı köhnəlmiş və ziddiyyətli yerləri tapır.
