# clonezilla-live-amd64-SME
 
### Clonezilla bootável com parâmetros predefinidos para conexão SSH

- Como modificar e compilar

> Você precisa utilizar um sistema GNU/Linux para isso

1. Faça as alterações necessárias com os parâmetros de inicialização nos arquivos ```boot/grub/grub.cfg```, ```syslinux/syslinux.cfg``` e ```syslinux/isolinux.cfg```.

2. Certifique-se de que os pacotes ```xorriso``` e ```isolinux``` estão instalados (```sudo apt install -y xorriso isolinux``` ou comando equivalente a sua distro)

3. Crie uma pasta temporária (por exemplo: ```mkdir /tmp/zip2iso```)

   3.1 Copie todos arquivos para a pasta criada
   
   3.2 Entre na pasta criada (```cd /tmp/zip2iso```)

4. Execute o comando ```xorriso -as mkisofs -R -r -J -joliet-long -l -cache-inodes -iso-level 3 -isohybrid-mbr /usr/lib/ISOLINUX/isohdpfx.bin -partition_offset 16 -A 'Clonezilla live CD' -b syslinux/isolinux.bin -c syslinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -eltorito-alt-boot --efi-boot boot/grub/efi.img -isohybrid-gpt-basdat -isohybrid-apm-hfsplus ./ > /tmp/clonezilla-live-amd64-SME.iso``` para criar a ISO

5. [Link](https://drbl.org/fine-print.php?path=./faq/2_System/87_create_clonezilla_iso_from_zip.faq#87_create_clonezilla_iso_from_zip.faq) para referência

> Opcional: [modificando Debian Live do Clonezilla](https://drbl.org/fine-print.php?path=./faq/2_System/81_add_prog_in_filesystem-squashfs.faq#81_add_prog_in_filesystem-squashfs.faq) (```live/filesystem.squashfs```)
