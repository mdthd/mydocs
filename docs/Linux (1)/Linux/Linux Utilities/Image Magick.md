# Image Magick

## Installing image magick on linux

### For Ubuntu

```bash
sudo apt install imagemagick
```

### For CentOS

```bash
sudo dnf install ImageMagick
```

:::info
EPEL should be enabled in the repositories
:::

### Check Version

```bash
convert --version
```

### Get Help

```bash
identify -help
```

### Get information of any image

```bash
identify /path/to/image
```

Get more information of image

```bash
identify -verbose /path/ti/image
```

Get width and height of image

```bash
identify -format '%wx%h' /path/to/file
```

### Resize images

```bash
convert input.jpg -resize 100x100 output.jpg
```

### Convert image file format

```bash
convert input.jpg -resize 100x100 output.png
```