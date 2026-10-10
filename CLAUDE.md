# CLAUDE.md

Bu fayl iş tərzini və layihə kontekstinin harada saxlandığını təsvir edir. Layihənin özü haqqında məlumat burada saxlanmır.

Aşağıdakı prosedurlar konteksti qorumaq üçündür, özlüyündə məqsəd deyil. Tapşırıq birmənalı və kiçikdirsə (bir düzəliş, qısa sual-cavab), müzakirə sənədində yalnız başlıq qalır və bəndlər açılmır; bunu bir sətirlə bildir. Prosedurun məqsədə xidmət etmədiyi başqa bir hal görsən, onu atla və səbəbini de.

## Layihə konteksti

| Yer | Məzmun |
| --- | --- |
| `docs/project/overview.md` | Layihə nədir, niyə var, nəyi əhatə edir. Nadir dəyişir. |
| `docs/project/status.md` | Hazırkı vəziyyət: harada dayanmışıq, növbəti addımlar, açıq suallar. Köhnə vəziyyətin üstünə yazılır, tarixçə git-də qalır. |
| `docs/decisions/` | Qəbul edilmiş qərarlar — hər müzakirə və ya mərhələ üçün bir fayl. |
| `.claude/discussions/` | Sessiyaların müzakirə sənədləri. |

- Sessiyanın əvvəlində `status.md`-ni oxu. Tarixi köhnədirsə, ona tam etibar etmə — `git log` ilə tutuşdur. `overview.md`-ni və qərarları mövzu tələb edəndə oxu.
- Koddan və ya git tarixçəsindən oxuna bilən məlumat bu sənədlərə yazılmır.

## Razılaşma

- Razılaşma yalnız istifadəçinin açıq təsdiqi ilə yaranır. Mövzunun dəyişməsi, düzəliş istənməsi, cavabsız qalma və ya ümumi müsbət ton razılaşma deyil.
- Qismən təsdiq yalnız təsdiqlənən hissəyə aiddir; qalan hissə açıq qalır.
- Təsdiqin nəyə aid olduğu aydın deyilsə, soruş.
- Bu qayda nəyin razılaşma və qərar kimi yazılacağına aiddir. Tapşırığı icra edərkən adi iş qərarları (adlandırma, fayl quruluşu, həll detalları) üçün təsdiq gözləmə — öz mühakiməni işlət.

## Müzakirə sənədi

- Hər sessiyanın əvvəlində `.claude/templates/discussion.md` formatında `.claude/discussions/YYYY-MM-DD-<mövzu>.md` faylı yarat. Mövzu sonradan aydınlaşırsa, faylın adını dəyiş.
- Hər fikir ayrıca bənddir: fikrin özü, istifadəçinin cavabı, modelin anlaması və status. Razılaşma olana qədər bənd yerində yenilənir; yeni bənd yalnız yeni fikir üçün açılır.
- Bənd təsdiqlənən kimi qərarı dərhal `docs/decisions/`-ə yaz. Vəziyyətə təsir edirsə, `status.md`-ni də yenilə. Sessiyanın sonunu gözləmə — sessiya istənilən an bitə bilər.
- Əvvəlki sessiyadan qalmış müzakirə sənədi tapsan, onun açıq bəndlərini istifadəçiyə qısaca göstər. Davam etdirilən bəndləri yeni sənədə köçür, köhnə sənədi sil — tarixçə git-də qalır.
- Kompaksiyadan sonra müzakirə sənədini yenidən oxu.

## Qərarlar

- Hər müzakirə və ya mərhələ üçün `.claude/templates/decision.md` formatında bir fayl yarat: `docs/decisions/YYYY-MM-DD-<mövzu>.md`. Qərarlar nömrələnmir.
- Qərarlar yalnız aydınlaşdırma üçün kontekstdir. Kod, sənədlər və digər qərarlar onlara istinad etmir, ona görə hər qərar özü-özlüyündə başa düşülən olmalıdır.
- Qəbul edilmiş qərarın mətni dəyişdirilmir. Qərar dəyişəndə yeni qərar yazılır və köhnə yanaşma onun rədd edilən alternativləri arasında, səbəbi ilə qeyd olunur. Köhnə qərarda yalnız status dəyişir: `ləğv edildi (YYYY-MM-DD)`.

## Auto memory

- Yaddaş bu repo-nun `.claude/memory/` qovluğundadır. Yönləndirməni `.claude/settings.local.json`-dakı `autoMemoryDirectory` edir. Bu fayl `.worktreeinclude` vasitəsilə worktree-lərə də köçürülür.
- Sistem promptundakı yaddaş yolu bu qovluq deyilsə (yeni maşın, konteyner, cloud sessiya), `.claude/memory/MEMORY.md`-ni özün oxu. Sonra istifadəçiyə `autoMemoryDirectory`-ni bu mühitdəki mütləq yola təyin etməyi təklif et.
- Yaddaşda yalnız istifadəçinin üstünlükləri, düzəlişləri və xarici istinadlar saxlanır (`user`, `feedback`, `reference`). Layihə biliyi yuxarıdakı sənədlərə yazılır, yoxsa eyni məlumat iki yerdə yaşayıb bir-birindən ayrılar.
- `MEMORY.md`-nin ilk sətrində son baxış tarixi yazılır (`—` hələ baxış olmadığını bildirir; onda ilk qeydin tarixindən say). O tarixdən 14 gündən çox keçibsə və yaddaş o vaxtdan dəyişibsə, işin təbii fasiləsində `/memory-review` təklif et.

## Bu faylı yeniləyərkən

- Qısa saxla. Fayl hər sessiyada yüklənir və hər sətir diqqət tələb edir.
- Qaydanın yanında səbəbini də yaz. Səbəbi bilən model kənar halları özü düzgün həll edir.
- "HƏMİŞƏ", "HEÇ VAXT" kimi sərt ifadələrdən qaç. İstisna yalnız həqiqətən geri dönməz nəticəsi olan hallardır.
- Mütləq icra olunmalı olan məhdudiyyətlər təlimatla deyil, hook və ya permission ilə həll olunur.
- Layihənin mərhələsi dəyişəndə (məsələn, dizayndan kod yazmağa keçid) bu quruluşun faydasını istifadəçi ilə birlikdə yoxla. Narahatlıq əlamətləri: sənədləşdirmə işin özünü üstələyir, lüzumsuz təsdiq sualları yaranır, `status.md` köhnəlir.
