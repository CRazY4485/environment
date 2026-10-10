# Qərarlar: iş mühitinin qurulması

Tarix: 2026-10-10

## Mühit layihə səviyyəsində, repo daxilində qurulur

- **Status:** qəbul edildi
- **Kontekst:** Layihəyə başlamazdan əvvəl Claude Code ilə iş mühiti (yaddaş, təlimatlar, kontekstin saxlanması) qurulmalı idi. Sual bu idi: mühit harada yaşayacaq və necə qurulacaq?
- **Qərar:** Mühit bu repo-nun içində, layihə səviyyəsində qurulur. Məzmunu ümumidir, konkret layihəyə görə yazılmayıb. Quraşdırma və ya sinxronizasiya skriptləri istifadə olunmur; mühit yalnız fayllardan ibarətdir.
- **Səbəb:** Repo ilə birlikdə hər maşına, worktree-yə və konteynerə keçir. Dəyişiklikləri git-də görünür. Skript olmadığı üçün saxlanması da sadədir.
- **Rədd edilən alternativlər:**
  - İstifadəçi səviyyəsində (`~/.claude`) ümumi konfiqurasiya — mühit layihə səviyyəsində olmalıdır; istifadəçi səviyyəsindəki fayllar repo ilə konteynerlərə keçmir.
  - Layihələrə tətbiq olunan şablon dəsti və JS skriptləri (tətbiq, bootstrap, SessionStart hook) — lazımsız mürəkkəblikdir; mühit birbaşa repo-da qurulmalıdır.

## CLAUDE.md sərt qaydalarla deyil, istiqamətlərlə yazılır

- **Status:** qəbul edildi
- **Kontekst:** CLAUDE.md-nin tonu modelin necə işlədiyinə təsir edir.
- **Qərar:** Model məhdudlaşdırılmadan işləməlidir. Sərt qadağalar və çərçivələr əvəzinə səbəbi göstərilmiş istiqamətlər yazılır.
- **Səbəb:** Səbəbi bilən model kənar halları özü düzgün həll edir. Sərt qadağalar isə ya həddən artıq, ya da yersiz tətbiq olunur.
- **Nəticələr:** Mütləq icra olunmalı olan məhdudiyyətlər təlimatla deyil, hook və ya permission ilə həll olunur.

## Layihə konteksti CLAUDE.md-də deyil, ayrıca quruluşda saxlanır

- **Status:** qəbul edildi
- **Kontekst:** Layihə haqqında bilik (nədir, vəziyyəti, qərarlar) bir yerdə saxlanmalı və sessiyalar arasında itməməlidir.
- **Qərar:** CLAUDE.md layihə konteksti üçün istifadə olunmur. Layihənin nə olduğu və son vəziyyəti ayrıca sənədlərdə, qərarlar isə ayrıca saxlanır.
- **Səbəb:** CLAUDE.md iş tərzini təsvir edir. Layihə məzmunu onunla qarışanda hər ikisi böyüyür və bir-birinə mane olur.
- **Rədd edilən alternativlər:**
  - CLAUDE.md-də "Layihə" bölməsi — layihə konteksti üçün ayrıca quruluş olmalıdır.

## Razılaşma yalnız açıq təsdiqlə yaranır

- **Status:** qəbul edildi
- **Kontekst:** Bir neçə təklifdən sonra istifadəçinin mövzunu dəyişməsi, düzəliş istəməsi və ya bir hissəni təsdiqləməsi səhvən "ümumi razılıq" kimi qəbul edilə bilər.
- **Qərar:** Razılaşma yalnız istifadəçinin açıq təsdiqi ilə yaranır. Mövzunun dəyişməsi, düzəliş istənməsi və ya qismən təsdiq ümumi razılaşma sayılmır. Qismən təsdiq yalnız təsdiqlənən hissəyə aiddir.
- **Səbəb:** Təsdiqlənməmiş fikrin qərar kimi yazılması yanlış xatırlamanın ən təhlükəli formasıdır, çünki o, sonradan fakt kimi qəbul edilir.

## Hər sessiyada strukturlu müzakirə sənədi aparılır

- **Status:** qəbul edildi
- **Kontekst:** Uzun sessiyalarda müzakirə unudulur və ya yanlış xatırlanır, xüsusən kontekst sıxışdırıldıqdan sonra.
- **Qərar:** Hər sessiyada müzakirə sənədi yaradılır və sessiyanın sonuna qədər aparılır. Hər fikir ayrıca bənddir: fikir qısa və aydın şəkildə yazılır, yanında istifadəçinin cavabı və modelin həmin cavabı necə anladığı qeyd olunur. Razılaşma olana qədər bənd yerində yenilənir; hər dəfə yeni bənd açılmır.
- **Səbəb:** "Modelin anlaması" sətri səhv anlamanı razılaşmaya çevrilmədən əvvəl görünən edir. Bəndlərin yerində yenilənməsi sətirlərin qarışmasının qarşısını alır. Sənədin xərci azdır, verdiyi fayda isə əvəzolunmazdır.
- **Rədd edilən alternativlər:**
  - Sənədi yalnız ehtiyac olanda yaratmaq — hər sessiyada yaratmaq problem deyil, sadəcə bir markdown faylıdır, fayda isə xərcdən çox böyükdür.

## Qərarlar müzakirə və ya mərhələ üzrə, nömrəsiz və istinadsız saxlanır

- **Status:** qəbul edildi
- **Kontekst:** Qərarlar səbəbləri və rədd edilən alternativlərlə birlikdə saxlanmalı, dəyişən və ləğv edilən qərarlar düzgün əks olunmalıdır.
- **Qərar:** Qərarlar müzakirəyə və ya mərhələyə görə qruplaşdırılır və nömrələnmir. Heç bir sənəd, kod və ya digər qərar onlara istinad etmir; qərarlar yalnız aydınlaşdırma üçün kontekst kimi istifadə olunur.
- **Səbəb:** İstinadlar layihə kontekstini bir-birinə bağlı sənədlər şəbəkəsinə çevirir.
- **Rədd edilən alternativlər:**
  - Nömrəli ADR-lər, indeks faylı və "əvəzləndi → N" istinadları — layihə kontekstini bir-birinə istinad edən sənədlərlə doldurur.
- **Nəticələr:** Qərar dəyişəndə köhnə yanaşma yeni qərarın rədd edilən alternativləri arasında səbəbi ilə yazılır. Köhnə qərarda yalnız status dəyişir. Tarixçə qorunur, istinad isə yaranmır.

## Layihə kontekstinin qovluq quruluşu

- **Status:** qəbul edildi
- **Kontekst:** Layihə konteksti, qərarlar və müzakirələr üçün konkret yerlər müəyyən edilməli idi.
- **Qərar:** Layihənin təsviri `docs/project/overview.md`, hazırkı vəziyyəti `docs/project/status.md`, qərarlar `docs/decisions/` qovluğunda saxlanır. Müzakirə sənədləri `.claude/discussions/`, onların və qərarların şablonları `.claude/templates/` qovluğundadır.
- **Səbəb:** `docs/` qovluğunu insanlar da oxuyur, ona görə o, Claude-a xas qovluqdan kənardadır. Müzakirə sənədləri və şablonlar isə Claude-un iş alətləridir.

## Müzakirə sənədləri git-də saxlanır

- **Status:** qəbul edildi
- **Kontekst:** Müzakirə sənədi müvəqqətidir; sual onun git-ə düşüb-düşməməsi idi.
- **Qərar:** `.claude/discussions/` qovluğu git ilə izlənir.
- **Səbəb:** Konteyner və ya sessiya gözlənilmədən bitəndə sənəd itmir. Müzakirənin tarixçəsi də qorunur.
- **Rədd edilən alternativlər:**
  - Qovluğu gitignored saxlamaq — sənəd konteynerlə birlikdə itə bilərdi.

## Auto memory repo daxilində və yalnız şəxsi qeydlər üçün

- **Status:** qəbul edildi
- **Kontekst:** Auto memory layihə səviyyəsində və steril saxlanmalı, layihə sənədləri ilə üst-üstə düşməməli idi.
- **Qərar:** Auto memory `.claude/settings.local.json`-dakı `autoMemoryDirectory` vasitəsilə repo-nun `.claude/memory/` qovluğuna yazılır və git ilə izlənir. Bu ayar `.worktreeinclude` vasitəsilə worktree-lərə köçürülür. Yaddaşda yalnız `user`, `feedback` və `reference` tipli qeydlər saxlanır; layihə biliyi `docs/` qovluğuna yazılır.
- **Səbəb:** Yaddaş repo ilə birlikdə hərəkət edir və dəyişiklikləri görünür. Layihə biliyinin tək bir mənbəyi olur.
- **Nəticələr:** `autoMemoryDirectory` mütləq yol tələb edir, ona görə yeni maşında və ya konteynerdə bu ayarı əl ilə təyin etmək lazımdır.

## Vəziyyət sənədi göstəriş vasitəsilə oxunur

- **Status:** qəbul edildi
- **Kontekst:** Claude `status.md`-ni ya CLAUDE.md-dəki göstəriş əsasında oxuya, ya da onu `@import` vasitəsilə avtomatik yükləyə bilərdi.
- **Qərar:** CLAUDE.md-də yalnız sessiyanın əvvəlində `status.md`-nin oxunması barədə göstəriş var; `@import` istifadə olunmur.
- **Səbəb:** Layihə məzmunu CLAUDE.md vasitəsilə yüklənmir və kontekstə daimi yük düşmür.
- **Rədd edilən alternativlər:**
  - `@import` — fayl hər sessiyada zəmanətlə yüklənərdi, amma layihə məzmunu CLAUDE.md vasitəsilə yüklənmiş olardı.
- **Nəticələr:** Claude-un faylı oxumağı ötürmə ehtimalı var.

## Quruluş saxlanılır, prosedurların tətbiq sərhədləri dəqiqləşdirilir

- **Status:** qəbul edildi
- **Kontekst:** Qurulan mühitin modelin iş prinsiplərini məhdudlaşdırıb-məhdudlaşdırmadığı rəsmi sənədlər, tədqiqatlar və icma təcrübəsi əsasında qiymətləndirildi. Qiymətləndirməyə görə prinsiplər hissəsi rəsmi tövsiyələrə uyğundur. Diktə edən isə prosedurların hər vəziyyətdə məcburi tətbiqidir: yeni modellər təlimatlara hərfi əməl etdiyi üçün prosedurlar faydasız olduqları yerdə də icra olunur.
- **Qərar:** Quruluş saxlanılır və üç düzəliş edilir. Birincisi, kiçik və birmənalı tapşırıqlarda müzakirə sənədində yalnız başlıq qalır; prosedurun məqsədə xidmət etmədiyi hallarda o, səbəbi bildirilərək atlanır. İkincisi, açıq təsdiq qaydası yalnız nəyin razılaşma və qərar kimi yazılacağına aiddir; icra zamanı adi iş qərarları üçün təsdiq gözlənilmir. Üçüncüsü, layihənin mərhələsi dəyişəndə quruluşun faydası istifadəçi ilə birlikdə yenidən yoxlanılır. Bundan əlavə, tarixi köhnə olan `status.md` `git log` ilə tutuşdurulur.
- **Səbəb:** Qərarların səbəbləri və rədd edilən alternativlər heç bir başqa yerdə saxlanmır. Kompaksiya isə məlumat itirir. Mənfi cəhətlər strukturun özündən deyil, onun məcburi tətbiqindən qaynaqlanır və strukturu atmadan aradan qaldırıla bilər.
- **Rədd edilən alternativlər:**
  - Quruluşdan tamamilə imtina — unutma və yanlış xatırlama problemi həll olunmamış qalardı.
  - Quruluşu dəyişmədən saxlamaq — prosedurlar kiçik tapşırıqlarda da hərfi icra olunar, lüzumsuz təsdiq sualları yarana bilərdi.
  - "Bu fayldakılar istiqamətdir, qadağa deyil" ümumi açıqlaması — konkret prosedurları zəiflətmir. Onun yerinə konkret atlama şərti yazıldı.
- **Nəticələr:** Quruluşun bu formada işlədiyini göstərən birbaşa sübut yoxdur. İlk sessiyalarda üç əlamət izlənməlidir: sənədləşdirmənin işi üstələməsi, lüzumsuz təsdiq sualları və `status.md`-nin köhnəlməsi.

## Mühit yeni layihələr üçün başlanğıc şablonudur

- **Status:** ləğv edildi (2026-10-10)
- **Kontekst:** Mühit hər yeni layihə üçün yenidən qurulmamalıdır.
- **Qərar:** Mühitin repo-su yeni layihələr üçün başlanğıc kimi istifadə olunur. Ona görə orada yalnız hər layihəyə aid olan ümumi məzmun saxlanır: CLAUDE.md, şablonlar, skill-lər, boş layihə sənədləri, boş yaddaş və mühitin qərarları (bu fayl). Mühitin qurulduğu sessiyanın müzakirə sənədi və vəziyyət qeydləri şablondan çıxarılıb.
- **Səbəb:** Hər yeni layihə eyni mühitlə və təmiz kontekstlə başlayır. Mühitin niyə belə qurulduğunu izah edən qərarlar isə onunla birlikdə gəlir.
- **Nəticələr:** Yeni layihə GitHub-ın "Use this template" funksiyası ilə yaradılanda şablonun git tarixçəsi köçmür. Adi `git clone` ilə isə tarixçə də köçür. Şablonun özü üzərində işləyərkən yazılan auto memory qeydləri bütün yeni layihələrə keçər, ona görə şablonda yaddaş boş saxlanmalıdır.

## Şablon mühitin repo-sunda ayrıca budaqda saxlanır

- **Status:** qəbul edildi
- **Kontekst:** Mühitin repo-su yeni layihələr üçün başlanğıc kimi istifadə olunur. Mühitin öz iş vəziyyəti (müzakirə sənədləri, vəziyyət, yaddaş) yeni layihənin təmiz başlanğıcından ayrılmalıdır, mühitin repo-su isə olduğu kimi qalmalıdır.
- **Qərar:** Mühitin repo-sunda iki budaq var. `master`-də mühit inkişaf etdirilir və onun iş vəziyyəti saxlanır. `template` budağı təmiz başlanğıcdır: layihə sənədləri və yaddaş boş skeletlərdir. O, GitHub-da default budaqdır və repo template kimi işarələnib. Yeni layihə "Use this template" ilə yaradılır. Mühit yalnız `master`-də dəyişdirilir. `template`-ə yalnız ümumi fayllar (CLAUDE.md, skill-lər, şablonlar, qərarlar, `.gitignore`, `.worktreeinclude`) `master`-dən fayl yolu ilə köçürülür, merge edilmir. `CLAUDE.md` və qərarlar həmişə birlikdə köçürülür.
- **Səbəb:** Yeni layihənin təmiz başlaması modelin təlimata əməl etməsindən deyil, quruluşun özündən asılı olur. "Use this template" mühitin git tarixçəsini köçürmür. Mühitin öz iş vəziyyəti toxunulmaz qalır.
- **Rədd edilən alternativlər:**
  - Tək budağı həmişə təmiz saxlamaq — mühitin öz müzakirə sənədləri və vəziyyəti üçün yer qalmır.
  - Layihə başlayanda təmizliyi təlimatla etmək — təmizlik modelin təlimata əməl etməsindən asılı olardı.
  - Budaqları merge ilə sinxronlaşdırmaq — mühitin vəziyyət faylları şablona keçərdi.
- **Nəticələr:** Repo-nu klonlayan şəxs `template` budağına düşür; mühit üzərində işləmək üçün `master`-ə keçmək lazımdır. Budaqlar əl ilə sinxronlaşdırılır. `master`-də silinən ümumi faylı `template`-dən də ayrıca silmək lazımdır, çünki fayl yolu ilə köçürmə silinmələri daşımır.

## Qərarlar ilə CLAUDE.md arasındakı ziddiyyət istifadəçiyə bildirilir

- **Status:** qəbul edildi
- **Kontekst:** Qərarlar və CLAUDE.md eyni iş qaydalarını təsvir edə bilər və bir-birindən ayrıla bilər. Bu, dörd halda baş verir: CLAUDE.md qərar yazılmadan dəyişdirilir; qərar yazılır, amma CLAUDE.md yenilənmir; şablon yenilənərkən fayllardan biri unudulur; yeni layihə şablondan miras qalan qaydanı qərar yazmadan dəyişir.
- **Qərar:** Qərar iş qaydasını dəyişirsə, CLAUDE.md eyni addımda, eyni commit-də yenilənir. Ziddiyyət görünəndə heç bir mənbə avtomatik üstün sayılmır: fərq tarixləri ilə birlikdə istifadəçiyə göstərilir və hansının qüvvədə olduğunu istifadəçi deyir.
- **Səbəb:** Ziddiyyətin istiqaməti hər dəfə fərqli olur: bəzən CLAUDE.md daha yenidir, bəzən qərar. Ona görə sabit üstünlük qaydası hallardan birində yanlış nəticə verir.
- **Rədd edilən alternativlər:**
  - "Ziddiyyətdə CLAUDE.md qüvvədədir" — qərar yazılıb CLAUDE.md yenilənməyəndə model köhnəlmiş qaydaya əməl edərdi.

## Mühitin repo-su public-dir, git müəllifi GitHub CLI hesabından götürülür

- **Status:** qəbul edildi
- **Kontekst:** Mühitin repo-su əvvəlcə private yaradılmışdı. Commit müəllifi isə yalnız bu repo üçün təyin edilmişdi, ona görə şablondan yaradılan yeni layihələrdə commit alınmayacaqdı.
- **Qərar:** Mühitin repo-su public-dir. Git müəllifi qlobal olaraq GitHub CLI-da daxil olunmuş hesabdan götürülür: ad hesabın adıdır, e-poçt isə hesabın GitHub noreply ünvanıdır. Autentifikasiya da GitHub CLI vasitəsilə aparılır (`gh auth git-credential`).
- **Səbəb:** Git hesabı GitHub CLI hesabı ilə eyni olmalıdır. Hesabın əsas e-poçtu GitHub-da gizlidir; o ünvanla edilən commit-lər push zamanı rədd oluna və public tarixçəyə düşə bilərdi.
- **Rədd edilən alternativlər:**
  - Hər repo üçün ayrıca lokal müəllif ayarı — yeni layihələrdə təkrar qurulmalı olardı.
  - Hesabın əsas e-poçtu — GitHub-da gizli işarələnib.
