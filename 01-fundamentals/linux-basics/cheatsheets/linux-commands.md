# Linux Commands Quick Reference

> Bu dosya `../../cheatsheets/linux-commands.md` dosyasının kopyasıdır.
> Ana cheat sheet'i oradan okuyabilirsiniz.

```bash
# Ana cheat sheet'i görüntüle
cat ../../cheatsheets/linux-commands.md
```

## En Çok Kullanılanlar

```bash
# Navigasyon
pwd                    # Neredeyim?
ls -lah                # Ne var?
cd /path               # Nereye gideyim?

# Dosya işlemleri
cat file.txt           # Oku
nano file.txt          # Düzenle
cp src dst             # Kopyala
mv old new             # Taşı/Yeniden adlandır
rm file.txt            # Sil

# Arama
find . -name "*.txt"   # Dosya ara
grep "pattern" file    # İçerik ara

# Yardım
man <command>          # Dokümantasyon
<command> --help       # Hızlı yardım
```

**Detaylı referans için:** `../../cheatsheets/linux-commands.md`
