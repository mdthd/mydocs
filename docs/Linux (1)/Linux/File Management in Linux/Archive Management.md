# Archive Management

## Archiving:

Grouping files together in single file, maintaining the directory structure

### To manage archives in Linux below commands are used

| Tool | Description | Common Extension | Compression Support | Notes |
| --- | --- | --- | --- | --- |
| `tar` | Standard archiver, used to group files | `.tar` | ❌ No | Can be combined with compressors (`gzip`, `xz`, etc.) |
| `cpio` | Archives files from input (e.g., `find` command) | `.cpio` | ❌ No | Often used in initramfs creation |
| `ar` | Used to archive object files (libraries) | `.a` | ❌ No | Common in C/C++ development |
| `pax` | POSIX archiver, supports multiple formats | `.pax` | ❌ No (default) | Can be configured for compression |
| `shar` | Shell archive – creates self-extracting script | `.sh` | ❌ No | Legacy; embeds files in shell script |