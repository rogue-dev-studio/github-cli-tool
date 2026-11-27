# GitHub CLI & Git Reference

Kumpulan perintah Git dan GitHub CLI (`gh`) yang sering digunakan, dikelompokkan berdasarkan fungsinya.

---

## 1. Git Dasar (Local & Remote)

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git init` | Menginisialisasi *repository* Git baru di folder saat ini. | `git init` |
| `git clone <url>` | Menyalin *repository* dari remote ke lokal. | `git clone https://github.com/user/repo.git` |
| `git status` | Melihat status file (staged, unstaged, untracked). | `git status` |
| `git add <file/folder>` | Memasukkan file atau folder tertentu ke *staging area*. | `git add app.js` |
| `git add .` | Memasukkan semua file yang berubah ke *staging area*. | `git add .` |
| `git commit -m "pesan"` | Menyimpan perubahan yang sudah di-*stage* ke *repository* lokal. | `git commit -m "feat: add login"` |
| `git checkout -b <nama>` | Membuat branch baru dan langsung berpindah ke branch tersebut. | `git checkout -b feat/login` |
| `git checkout master` | Berpindah kembali ke branch *master*. | `git checkout master` |
| `git push -u origin <branch>` | Mengunggah branch ke remote (`origin`) dan menetapkan *tracking* branch. | `git push -u origin feat/login` |
| `git branch -d <branch>` | Menghapus branch lokal (hanya jika sudah di-*merge*). | `git branch -d feat/login` |
| `git push origin --delete <branch>` | Menghapus branch di remote repository (GitHub). | `git push origin --delete feat/login` |

## 2. Git Log & Inspection

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git log` | Melihat riwayat commit. | `git log` |
| `git log --oneline` | Riwayat commit dalam satu baris (singkat). | `git log --oneline` |
| `git log -p` | Riwayat commit disertai detail perubahan (*patch*). | `git log -p` |
| `git log --graph` | Melihat struktur branch secara visual (grafik). | `git log --graph` |
| `git log --since="2026-01-01"` | Melihat commit setelah tanggal tertentu. | `git log --since="2026-01-01"` |
| `git log --until="2026-12-31"` | Melihat commit sebelum tanggal tertentu. | `git log --until="2026-12-31"` |
| `git log --since="1 week ago"` | Melihat commit dalam rentang waktu relatif. | `git log --since="1 week ago"` |
| `git log --after="2026-01-01" --before="2026-06-01"` | Melihat commit dalam rentang tanggal. | `git log --after="2026-01-01" --before="2026-06-01"` |

## 2b. Git Fetch & Sync (Remote)

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git fetch` | Mengundang data terbaru dari remote tanpa merge. | `git fetch origin` |
| `git fetch --all` | Mengundang data dari semua remote. | `git fetch --all` |
| `git fetch --prune` | Hapus referensi branch remote yang sudah dihapus. | `git fetch --prune` |
| `git pull` | Mengundang dan langsung merge ke branch saat ini. | `git pull origin master` |
| `git pull --rebase` | Mengundang dan rebase bukan merge. | `git pull --rebase` |

## 3. Git Advanced & History Cleanup

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git cherry-pick <hash>` | Mengambil commit spesifik dari branch lain. | `git cherry-pick abc1234` |
| `git commit --amend -m "<new msg>"` | Mengubah pesan commit terakhir tanpa commit baru. | `git commit --amend -m "pesan baru"` |
| `git push --force` | Memaksa push ke remote. Gunakan setelah `amend`. | `git push --force` |
| `git push --force-with-lease` | Push aman yang gagal jika remote sudah berubah. | `git push --force-with-lease` |

## 4. GitHub CLI (`gh`)

### 4.1 Authentication

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `gh auth login` | Melakukan otentikasi akun GitHub di terminal. | `gh auth login` |
| `gh auth status` | Memeriksa status login akun GitHub. | `gh auth status` |

### 4.2 Repository

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `gh repo clone <owner>/<repo>` | *Clone repository* GitHub via CLI. | `gh repo clone rogue-dev-studio/github-cli-tool` |
| `gh repo create` | Membuat *repository* baru di GitHub via terminal. | `gh repo create my-app` |

### 4.3 Pull Requests

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `gh pr list` | Melihat daftar *Pull Request* yang aktif. | `gh pr list` |
| `gh pr create` | Membuat *Pull Request* baru. | `gh pr create` |
| `gh pr checkout <number>` | Mengambil/pindah ke branch *Pull Request* tertentu. | `gh pr checkout 12` |
| `gh pr view <number>` | Melihat detail *Pull Request*. | `gh pr view 12` |

### 5. Git Lainnya (Daily Use & Undo)

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git diff` | Lihat perbedaan antara working tree dan staging. | `git diff` |
| `git diff --cached` | Lihat perbedaan antara staging dan last commit. | `git diff --cached` |
| `git diff <branch1> <branch2>` | Bandingkan dua branch. | `git diff master feat/login` |
| `git show <hash>` | Lihat detail spesifik commit. | `git show abc1234` |
| `git blame <file>` | Lihat siapa yang mengubah setiap baris file. | `git blame app.js` |
| `git reset --soft <hash>` | Kembalikan HEAD, simpan perubahan di staging. | `git reset --soft HEAD~1` |
| `git reset --mixed <hash>` | Kembalikan HEAD + staging (default). | `git reset --mixed HEAD~1` |
| `git reset --hard <hash>` | Kembalikan HEAD, staging, dan working tree (hapus semua). | `git reset --hard HEAD~1` |
| `git restore <file>` | Kembalikan file ke keadaan terakhir di staging. | `git restore app.js` |
| `git revert <hash>` | Buat commit baru yang membatalkan commit tertentu. | `git revert abc1234` |
| `git stash` | Simpan sementara perubahan yang belum di-commit. | `git stash` |
| `git stash pop` | Kembalikan perubahan dari stash terakhir. | `git stash pop` |
| `git stash list` | Lihat daftar stash yang tersimpan. | `git stash list` |
| `git tag <nama>` | Buat tag untuk versi rilis. | `git tag v1.0.0` |
| `git push --tags` | Kirim semua tag ke remote. | `git push --tags` |
| `git remote -v` | Lihat daftar remote yang terkonfigurasi. | `git remote -v` |
| `git remote add <nama> <url>` | Tambahkan remote baru. | `git remote add upstream https://...` |
## 5. Git Configuration (Setup & Settings)

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `git config --global user.name "<nama>"` | Mengatur nama pengguna Git secara global. | `git config --global user.name "Aris"` |
| `git config --global user.email "<email>"` | Mengatur email pengguna Git secara global. | `git config --global user.email "aris@example.com"` |
| `git config --global core.editor "<editor>"` | Mengatur *text editor* default untuk commit message. | `git config --global core.editor "code --wait"` |
| `git config --list` | Melihat semua konfigurasi Git yang aktif. | `git config --list` |
| `git config --local <key> <value>` | Mengatur konfigurasi spesifik hanya untuk repository ini. | `git config --local user.email "work@email.com"` |
| `git config --global --unset <key>` | Menghapus konfigurasi global tertentu. | `git config --global --unset user.name` |


## 6. GitHub CLI (`gh`) — Lanjutan

### 6.1 Workflow & Actions

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `gh workflow list` | Daftar workflow GitHub Actions. | `gh workflow list` |
| `gh workflow run <id>` | Jalankan workflow secara manual. | `gh workflow run ci.yml` |
| `gh run list` | Lihat daftar run workflow. | `gh run list` |
| `gh run view <id>` | Lihat detail satu run workflow. | `gh run view 123` |

### 6.2 Search & API

| Perintah | Kegunaan | Contoh |
|:---|:---|:---|
| `gh search repos <query>` | Cari repository di GitHub. | `gh search repos "ai-agents"` |
| `gh search issues <query>` | Cari issue di GitHub. | `gh search issues "bug login"` |
| `gh api <endpoint>` | Panggil GitHub API langsung via CLI. | `gh api /user/repos` |
