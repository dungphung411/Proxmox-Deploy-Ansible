# A. Thư Viện Ansible

## Ansible-Galaxy là gì?

Sứ mệnh của nhóm  Ansible Proxmox Community là làm cho việc tự động hóa Proxmox bằng Ansible trở nên dễ dàng hơn, tốt hơn và tự động hóa hơn bao giờ hết!  
Chúng tôi hoan nghênh các thành viên ở mọi trình độ kỹ năng tham gia tích cực vào cộng đồng cởi mở, hòa nhập và năng động này.  
Dù bạn là chuyên gia hay chỉ mới bắt đầu hành trình của mình với Ansible và Proxmox, bạn đều được khuyến khích đóng góp, chia sẻ hiểu biết và hợp tác cùng những người đam mê khác.

## Requirements
| #             |  Yêu cầu                                                  |  Ghi chú                       | 
|---------------|-----------------------------------------------------------|--------------------------------|
| Node Proxmox  |  python3-pip, proxmoxer, requests, user ansible, SSH key  |  Cho phép chạy module qua SSH  |
| Control node  |  Ansible, collection proxmox-galaxy, proxmoxer, requests  |  Điều khiển và gọi API Proxmox | 
|---------------|-----------------------------------------------------------|--------------------------------|
- Các node Proxmox đều cần cài Python3 và Pip, tiếp đến là proxmoxer và requests.

```bash
apt install python3-pip sudo -y
pip3 install proxmoxer requests
```
- Tạo user ansible và tạo ssh-key từ node Ansible control
```bash
adduser ansible
usermod -a -G sudo ansible
```

```bash
ssh-keygen -t rsa -b 4096 -C "ansible-key" -f ~/.ssh/id_rsa -N ""
ssh-copy-id ansible@<IP_Node1>
ssh-copy-id ansible@<IP_Node2>
ssh-copy-id ansible@<IP_Node3>

```

- Ở jump server, hoặc server điều khiển Ansible, cài Ansible và toàn bộ collection

```bash
 sudo apt update
 sudo apt install software-properties-common
 sudo add-apt-repository --yes --update ppa:ansible/ansible
 sudo apt install ansible
```
- Version Ansible cần thiết là >=2.17.0, kiểm tra trước version cho chắc.

```bash
ansible-galaxy collection install community.proxmox
ansible-galaxy collection install community.proxmox --upgrade
```
- Yêu cầu phiên bản Python >= 3.7 và Proxmoxer >= 2.0 nữa để chạy ansible.
## Cách cài đặt
- Viết file inventory.yaml để check ra số lượng node cần quản lí
- Phân ra 1 máy original để tạo cụm cluster và các máy còn lại sẽ join


## Tài liệu tham khảo 
- [Ansible-Galaxy](https://galaxy.ansible.com/ui/repo/published/community/proxmox/)