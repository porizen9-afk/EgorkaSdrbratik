import os, zipfile, pathlib, shutil

# paths of uploaded images
srcs = [
    "/mnt/data/IMG_20251119_205027_322.jpg",
    "/mnt/data/IMG_20251119_205027_759.jpg",
    "/mnt/data/IMG_20251119_205027_359.jpg"
]

# Prepare site dir
base = pathlib.Path("/mnt/data/EgorkaSdrbratik_final")
if base.exists():
    shutil.rmtree(base)
base.mkdir()

# Copy previous generated site content? Recreate minimal site by copying previous zip? Instead, reuse previous dir if exists?
# I'll rebuild structure quickly using same earlier generated folder EgorkaSdrbratik_site
old = pathlib.Path("/mnt/data/EgorkaSdrbratik_site")
shutil.copytree(old, base, dirs_exist_ok=True)

# replace first 3 placeholder photos
imgdir = base/"images"
for i, src in enumerate(srcs, start=1):
    shutil.copy(src, imgdir/f"photo{i}.jpg")

# create zip
zip_path = "/mnt/data/EgorkaSdrbratik_FINAL.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for f in base.rglob("*"):
        z.write(f, arcname=str(f.relative_to(base)))

zip_path
import os, zipfile, pathlib, shutil

# paths of uploaded images
srcs = [
    "/mnt/data/IMG_20251119_205027_322.jpg",
    "/mnt/data/IMG_20251119_205027_759.jpg",
    "/mnt/data/IMG_20251119_205027_359.jpg"
]

# Prepare site dir
base = pathlib.Path("/mnt/data/EgorkaSdrbratik_final")
if base.exists():
    shutil.rmtree(base)
base.mkdir()

# Copy previous generated site content? Recreate minimal site by copying previous zip? Instead, reuse previous dir if exists?
# I'll rebuild structure quickly using same earlier generated folder EgorkaSdrbratik_site
old = pathlib.Path("/mnt/data/EgorkaSdrbratik_site")
shutil.copytree(old, base, dirs_exist_ok=True)

# replace first 3 placeholder photos
imgdir = base/"images"
for i, src in enumerate(srcs, start=1):
    shutil.copy(src, imgdir/f"photo{i}.jpg")

# create zip
zip_path = "/mnt/data/EgorkaSdrbratik_FINAL.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for f in base.rglob("*"):
        z.write(f, arcname=str(f.relative_to(base)))

zip_path
