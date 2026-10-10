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
- **İstifadəçinin cavabı:** —
- **Modelin anlaması:** Görünürlük, ad və müəllif e-poçtu istifadəçi tərəfindən təsdiqlənməyib.
- **Status:** açıq
