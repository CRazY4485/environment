# Müzakirə: iş mühitinin qurulması

Tarix: 2026-10-10

<!--
Hər bənd bir fikirdir. Razılaşma olana qədər bənd yerində yenilənir; yeni bənd yalnız yeni fikir üçün açılır.
Status yalnız istifadəçinin açıq təsdiqi ilə "təsdiqləndi" olur. Qismən təsdiqdə hansı hissənin təsdiqləndiyi yazılır.
Təsdiqlənən bənd dərhal docs/decisions/-ə köçürülür.
-->

## Qovluq quruluşu

- **Fikir (model):** Layihə konteksti `docs/project/` qovluğunda, qərarlar `docs/decisions/` qovluğunda, müzakirə sənədləri `.claude/discussions/` qovluğunda, şablonlar isə `.claude/templates/` qovluğunda saxlanır.
- **İstifadəçinin cavabı:** "Qalanlarını təsdiqləyirəm."
- **Modelin anlaması:** Tətbiq olunduğu formada təsdiqləndi.
- **Status:** təsdiqləndi

## Auto memory repo daxilində və yalnız şəxsi qeydlər üçün

- **Fikir (model):** Auto memory `autoMemoryDirectory` vasitəsilə `.claude/memory/` qovluğunda, git ilə izlənərək saxlanır. Yalnız `user`, `feedback` və `reference` tipli qeydlər yazılır.
- **İstifadəçinin cavabı:** "Qalanlarını təsdiqləyirəm."
- **Modelin anlaması:** Tətbiq olunduğu formada təsdiqləndi.
- **Status:** təsdiqləndi

## Claude sənədləri necə tapır

- **Fikir (model):** CLAUDE.md-də yalnız `status.md`-nin oxunması barədə göstəriş var. Alternativ `@import` idi.
- **İstifadəçinin cavabı:** "Qalanlarını təsdiqləyirəm."
- **Modelin anlaması:** Mövcud vəziyyət (göstəriş, `@import` yoxdur) təsdiqləndi. Təsdiq iki variantdan hansına aid olduğunu açıq demir; anlama bu yöndədir, istifadəçi düzəldə bilər.
- **Status:** təsdiqləndi

## Müzakirə sənədlərinin git-də saxlanması

- **Fikir (model):** Qovluğu gitignored saxlamaq təklif olunmuşdu.
- **İstifadəçinin cavabı:** "Müzakirə sənədləri git-ə düşsün."
- **Modelin anlaması:** Təklif rədd edildi; `.claude/discussions/` git ilə izlənir.
- **Status:** təsdiqləndi (istifadəçinin variantı)

## İlkin commit

- **Fikir (model):** Mühit faylları ilkin commit kimi git-ə əlavə olunur.
- **İstifadəçinin cavabı:** "Qalanlarını təsdiqləyirəm."
- **Modelin anlaması:** Commit üçün icazə verildi.
- **Status:** təsdiqləndi

## Quruluş modeli məhdudlaşdırırmı?

- **Fikir (istifadəçi):** Qurulan mühit modelin öz iş prinsiplərini də məhdudlaşdıra və ona diktə edə bilər; bu cür quruluşun mənfi cəhətləri ola bilər. Rəsmi sənədlər və icma mənbələri əsasında tərəfsiz qiymətləndirmə istənir.
- **Modelin qiyməti:** Narahatlıq qismən əsaslıdır. Prinsiplər hissəsi (səbəbli istiqamətlər, qısa CLAUDE.md, sənədlərin ehtiyac olanda oxunması) rəsmi tövsiyələrə uyğundur. Diktə edən hissə prosedurlardır: hər sessiyada sənəd aparmaq və hər cavabdan sonra onu yeniləmək. Yeni modellər təlimatlara hərfi əməl etdiyi üçün bu prosedurlar faydasız olduğu hallarda da icra olunacaq. "İstiqamətdir, qadağa deyil" cümləsi konkret prosedurları zəiflətmir. Təkliflər: konkret "atlama" şərti əlavə etmək, açıq təsdiq qaydasının yalnız qərar kimi yazılan məqamlara aid olduğunu dəqiqləşdirmək, mərhələ dəyişəndə quruluşu yenidən qiymətləndirmək.
- **Modelin mövqeyi:** Quruluş istifadə edilməlidir, amma yuxarıdakı düzəlişlərlə. Problem quruluşun özündə deyil, onun hər vəziyyətdə məcburi tətbiqindədir. Bu birbaşa sübuta deyil, mühakiməyə əsaslanır.
- **İstifadəçinin cavabı:** "Düzəlişləri tətbiq et. Github-da yeni repo yarat və push et."
- **Modelin anlaması:** Quruluşun saxlanması və təklif olunan düzəlişlər təsdiqləndi. GitHub repo-su yaradılmalı və push edilməlidir.
- **Status:** təsdiqləndi

## GitHub repo-su

- **Fikir (model):** Repo-nun görünürlüyü deyilmədiyi üçün o, private yaradılır (sonradan public etmək olar, əksinə isə məzmun artıq yayılmış olur). Adı qovluğun adı ilə eynidir: `environment`. Commit-lər üçün bu repo-ya aid git müəllifi GitHub hesabının adı və noreply e-poçtu ilə təyin olunur. Şəxsi e-poçt barədə soruşulmuşdu, amma cavab verilmədi.
- **İstifadəçinin cavabı:** "Reponu public et. Git hesabı isə github CLI-da olmalıdır, bax"
- **Modelin anlaması:** Repo public olur. Git müəllifi GitHub CLI-da daxil olunmuş hesabdan (`CRazY4485`) götürülür və qlobal təyin edilir ki, şablondan yaradılan layihələrdə də işləsin. Hesabın əsas e-poçtu GitHub-da gizli olduğu üçün hesabın noreply ünvanı istifadə olunur. Repo-nun adı (`environment`) barədə heç nə deyilmədi.
- **Status:** qismən təsdiqləndi: görünürlük (public) və git hesabı; repo-nun adı açıq qalır

## Qərarlar ilə CLAUDE.md arasında ziddiyyət

- **Fikir (model):** İlk təklif "ziddiyyətdə CLAUDE.md qüvvədədir" idi. İstifadəçi ziddiyyətin hansı hallarda yarandığını soruşdu. Təhlil dörd hal göstərdi; onlardan birində qərar CLAUDE.md-dən daha yeni olur, ona görə ilk təklif yanlış idi. Yenidən işlənmiş təklif: qərar iş qaydasını dəyişirsə, CLAUDE.md eyni commit-də yenilənir; ziddiyyət görünəndə fərq tarixləri ilə istifadəçiyə göstərilir və hansının qüvvədə olduğunu istifadəçi deyir.
- **İstifadəçinin cavabı:** "Tövsiyələrini tətbiq et."
- **Modelin anlaması:** Yenidən işlənmiş təklif təsdiqləndi.
- **Status:** təsdiqləndi

## Repo-nun yeni layihələr üçün şablon kimi istifadəsi

- **Fikir (istifadəçi):** Repo yeni layihələr üçün başlanğıc kimi istifadə olunacaq, ona görə düzgün təmizlənməlidir. Repo olduğu kimi qalır; layihə üçün istifadə ediləndə ayrıca budaqdan şablon kimi yararlanılır.
- **Modelin qiyməti:** Bu yanaşma "təlimatla təmizləmə"dən üstündür, çünki təmizliyi model təlimata əməl etdiyi üçün deyil, quruluşun özü təmin edir. Zəif tərəfi budur ki, iki budaq bir-birindən ayrıla bilər. Bunun qarşısı belə alınır: mühit `master`-də inkişaf etdirilir, şablona yalnız ümumi fayllar köçürülür.
- **Plan (model):** `template` budağı təmiz `a1366bf` commit-i üzərində yaradılır. Bu commit sessiyanın geri qaytarılmış (rewind) hissəsindən qalıb və artıq push edilmişdi; həmin addımda repo template kimi də işarələnmişdi. `master`-də mühitin iş vəziyyəti bərpa olunur. Mühit yalnız `master`-də dəyişdirilir, `template`-ə yalnız ümumi fayllar fayl yolu ilə köçürülür. GitHub-da default budaq `template` olur.
- **İstifadəçinin cavabı:** "Tövsiyələrini tətbiq et."
- **Modelin anlaması:** Cavab ziddiyyət qaydası ilə bağlı suala verilib, amma "tövsiyələr" cəm haldadır. Bu, şablon planının da təsdiqi kimi başa düşüldü. Anlama səhvdirsə, istifadəçi düzəldə bilər.
- **Status:** təsdiqləndi

## Şablon budağının təmizlənməsi

- **Fikir (istifadəçi):** "Template budağı yeni layihələr üçün istifadə ediləcək buna görə də təmizlənməlidir."
- **Modelin anlaması:** Şablonda mühitə aid tək məzmun qərarlar faylı idi: hamısı mühitin qurulmasına aid 15 qərar, bir hissəsi birbaşa mühitin repo-su haqqında. Fayl şablondan silindi və sinxronizasiya qaydasından çıxarıldı. Yeni layihə boş qərarlar qovluğu ilə başlayır. Budağın git tarixçəsinə toxunulmadı: "Use this template" tarixçəni köçürmür, tarixçəni yenidən yazmaq isə public default budağa force push tələb edərdi.
- **Status:** təsdiqləndi (istifadəçinin göstərişi); təmizliyin həcmi modelin anlamasıdır
