# cleanup-incus
repository to document how to cleanup incus for development environment

## Path where incus is stored and should be deleted to purge incus

### dir where instance, images and db are stored
sudo rm -rf /var/lib/incus/

### dir where logs are stored
sudo rm -rf /var/log/incus/

### dir where settings are stored
rm -rf ~/.config/incus/

## Bridges are remaining on environment?

### Check ip link and clean them up
ip link show | grep incus
sudo ip link delete incusbr0

## Mountpoints are remaining on environment?

### Check mountpoint and clean them up
mount | grep incus
sudo umount -l /var/lib/incus/guestapi
sudo umount -l /var/lib/incus/shmounts

## nftables are remaining on environment?

### Check nftables and clean them up
sudo nft list tables
sudo nft delete table inet incus
sudo nft delete table inet lxc
sudo nft delete table ip lxc
