Kickstart file for Fedora 42 (Dec 2025).

You will need to replace the USERNAME, ENCRYPTED_PASSWORD and the sda values below to comply with your actual setup. To generate a secure hashed password: `mkpasswd -m sha-512`.

To generate the actual ISO you can use the below command:
```
# xorriso -as mkisofs \
    -V 'Fedora-E-dvd-x86_64-42' \
    --grub2-mbr /mnt/modified_iso/boot/grub2/i386-pc/boot_hybrid.img \
    --protective-msdos-label \
    -partition_cyl_align off \
    -partition_offset 16 \
    -partition_hd_cyl 64 \
    -partition_sec_hd 32 \
    -append_partition 2 28732ac11ff8d211ba4b00a0c93ec93b /mnt/modified_iso/images/efiboot.img \
    -appended_part_as_gpt \
    -iso_mbr_part_type a2a0d0ebe5b9334487c068b6b72699c7 \
    --boot-catalog-hide \
    -b 'images/eltorito.img' \
    -no-emul-boot \
    -boot-load-size 4 \
    -boot-info-table \
    --grub2-boot-info \
    -eltorito-alt-boot \
    -e images/efiboot.img \
    -no-emul-boot \
    -o new-fedora-custom.iso \
    /mnt/modified_iso
```

Detailed instructions on how to use this and relevant commands can be found [on my website](https://96-fromsofia.net/posts/fedora42-iso/).
