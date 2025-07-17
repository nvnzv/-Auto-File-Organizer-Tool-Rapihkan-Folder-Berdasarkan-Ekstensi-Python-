# AUTO FILE ORGANIZER BASIC
# Navanza Digital Lab
# Cara pakai:
# 1. Jalankan script ini (python organizer.py)
# 2. Masukkan path folder target saat diminta
# 🔥 Untuk versi premium dengan GUI dan log hasil, beli di Lynk: https://lynk.id/navanza

import os
import shutil

def organize_by_extension(folder_path):
    for filename in os.listdir(folder_path):
        file_path = os.path.join(folder_path, filename)
        if os.path.isfile(file_path):
            ext = filename.split(".")[-1].lower()
            ext_folder = os.path.join(folder_path, ext)
            if not os.path.exists(ext_folder):
                os.makedirs(ext_folder)
            shutil.move(file_path, os.path.join(ext_folder, filename))
            print(f"[+] {filename} --> {ext}/")

if __name__ == "__main__":
    target_folder = input("Masukkan path folder target: ")
    organize_by_extension(target_folder)
    print("[✓] Folder berhasil dirapikan berdasarkan ekstensi.")
