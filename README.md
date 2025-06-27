# View-the-passwords-of-all-Wi-Fi-networks-authorized-on-your-machine.



import socket
import ipaddress

network = ipaddress.ip_network('192.168.0.0/24', strict=False)

for ip in network.hosts():
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(0.5)
        result = sock.connect_ex((str(ip), 80))
        if result == 0:
            print(f"Host {ip} has port 80 open.")
        sock.close()
    except Exception as e:
        print(f"Error on {ip}: {e}")



           
