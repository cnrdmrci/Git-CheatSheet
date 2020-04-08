# Git Cheat Sheet

### Git Kulumu
https://git-scm.com/downloads adresinden indirilerek kurulabilir.

### Komut: git config
Git kurulumundan sonra yapılandırma ayarları için kullanılır.
> git config --global user.name "isim"\
> git config --global user.email "email"

### Komut: git init
İlgili dizinde yerel bir depo oluşturmak için kullanılır.

### Komut: git add
İlgili dizindeki yerel depoya eklenecek dosyaları belirlemek için kullanılır.
> git add . 
> git add README.md

### Komut: git commit
İlgili dizindeki yerel depoya seçili dosyaları bilgi mesajı ile birlikte eklemek için kullanılır.
> git commit -m "First commit"\
> git commit --amend -m "Edit commit" //Son commitin adını değiştirir.

### Komut: git remote
İlgili dizindeki yerel depoyu göndereceğimiz uzak depo adresini belirlemek için kullanılır.
> git remote add origin https://github.com/cnrdmrci/Git-CheatSheet.git

### Komut: git clone
Uzak adresdeki depoyu yerel bilgisayara indirmek için kullanılır.
> git clone https://github.com/cnrdmrci/Git-CheatSheet.git

----------------------------------------------------------------------------------------------
### Komut: git branch -av
Tüm branch'leri listeler.

### Komut: git branch newBranch
Yeni branch oluşturmak için kullanılır.
> git branch newBranch\
Branch silmek için ise\
> git branch -d newBranch //delete locally\
> git branch -d -r origin/newBranch\
> git push origin --delete newBranch //delete remotely

### Komut: git checkout newBranch
Farklı dala geçmek için kullanılır.
> git checkout newBranch
-b eklendiğinde yeni bir branch oluşturulur ve o branch üzerinde işleme devam edilir.\
Uzak depodaki bir brach'i getirme
> git checkout --track origin/newBranch


### Komut: git merge
newBranch adında bir branch oluşturduk. Değişiklik yaptık. newBranch üzerindeyken master branch'ini merge ettik.Conflict oluşursa düzelttik. Ardından master branch'ine newBranch'i merge ettik.

> (on branch newBranch)$ git merge master\
> (resolve any merge conflicts if there are any)\
> git checkout master\
> git merge newBranch (there won't be any conflicts now)

### Komut: git mergetool
Oluşan conflict'leri düzeltmek için kullanılmaktadır.\
Ön ayarlar;
> git config merge.tool vimdiff\
> git config merge.conflictstyle diff3\
> git config mergetool.prompt false

> git mergetool

<pre>
  ╔═══════╦══════╦════════╗
  ║       ║      ║        ║
  ║ LOCAL ║ BASE ║ REMOTE ║
  ║       ║      ║        ║
  ╠═══════╩══════╩════════╣
  ║                       ║
  ║        MERGED         ║
  ║                       ║
  ╚═══════════════════════╝
</pre>

> :diffg RE\
> :diffg BA\
> :diffg LO\
> :wqa\
> git commit -m "message"\
> git clean
Remove extra files (e.g. .orig) created by diff tool.

### Komut: git tag
> git checkout (commitId) //ile belirli bir zamanda atılan commitin zamanına dönebililiyoruz.\
> tig //ile detalı anlık inceleme yapabiliyoruz.\
> git tag -a test.v1 -m "add test tag"	//Şeklinde ilgili committe tag oluşturabiliyoruz.\
> git tag -l ya da git tag --list 	//Depoda kayıtlı tag’leri listelemek için kullanılır.\
> git tag -d (tagAdi) //Bir tag’i depodan silmek için kullanılır.\
> git push --tags //Uzak depoya tagları eklemek için kullanılır.\
> git checkout -b newBrancName 	//Şeklinde ilgili tagı farklı bir branch'e alabilir ve geliştirmeye devam edebiliriz.

### Komut: git rebase
git merge komutu gibi branch'lerin birleştirilmesinde kullanılır. newBranch'a masterı merge ettiğimizde masterdaki yeni değişiklikler newBranch'e yeni commitler olarak eklenirken, git rebase komutu newBranch'in başlangıç adresini master'ın son commiti olarak değiştirerek birleştirme yapar.
> git rebase master

Commit mesajını değiştirmek için aşağıdaki ifade kullanılır. Son 4 commiti göstermesini aşağıda sağladık.
> git rebase -i HEAD~4
Açılan pencerede değiştirmek istediğimiz mesajın başına 'r' koyuyoruz kaydedip çıkıyoruz.\
Ardından açılan pencerede mesajı değiştiriyoruz ve kaydediyoruz. Sonuç olarak değişen bir commit elde ediyoruz.


### Komut: git status
Commitlenmemiş tüm değişiklikleri gösterir.
> git status
Detaylı gösterim için
> git status -vv

### Komut: git diff
Temel dosya ile olan farklılıkları gösterir.
Branch'ler arası farklılıkları yada staged durumdaki farklılıkları da gösterebilir.
> (On master branch)$ git diff newBranch
> git diff --staged

### Komut: git log
Tüm commitleri detaylı bir şekilde listeler.
> git log
Tüm commitleri sadece bir şekilde listeler.
> git log --oneline

### Komut: git blame
Belirtilen dosyadaki tüm satırların değişimi hakkında tek tek bilgi verir.
> git blame README.md

### Komut: git revert
Bir committeki değişiklikleri geri alan bir commit oluşturur.
> git revert (commitId)

### Komut: git reset
Unstage everything - retain changes:
> git reset
Discard all local changes, but save them for later:
> git stash
Discard everything permanently:
> git reset --hard
Commit silinir ilgili değişiklik stage durumunda olur.
> git reset --soft (commitId)
Staged durumundaki dosya unstaged olur.
> git reset test.txt
İlgili commitId'den sonraki commitleri siler.
> git reset (commitId)

### Komut: git rm
.gitignore'a eklenen ve hala kontrol altında olan dosyayı çıkartmak için;
> git rm --cached test.txt
Dosya gerçekte silinmedi. Sadece versiyon kontrol sisteminin dışında bırakıldı.

### Komut: git show
İlgili committi detaylı bir şekilde gösterir.
> git show (commitId)
İlgili dosyanın son commitini detaylı bir şekilde gösterir.
> git show README.md

### Komut: git pull
Uzak adresdeki deponun son değişikliklerini yerel bilgisayarla eşlemek için kullanılır.
> git pull

### Komut: git push
İlgili dizindeki yerel depoyu uzak depo adresine iletmek için kullanılır.
> git push -u origin master

### Komut: git stash
Acil bir durumda değişiklik yapılan dosyaları zulaya atıp daha sonra geriye almaktır.
> git stash //Değiştirilen dosyaları zulaya atar.\
> git stash pop 1 //Zuladaki dosyaları geri yükler.\
> git stash save "stashName"\
> git stash drop 1\
> git stash list\
> git stash show -p 0\
> git stash -p\
> git stash drop stash@{1}\
> git stash clear //delete all of your stashes with
