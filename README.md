# -Python-Network-Scanner-Port-Scanner-
#A simple Python script can be written to scan for open ports on a remote host. This can be helpful in penetration testing to identify open ports and services that might be vulnerable to attack
import socket

def scan_ports(target):
    # Define the range of ports to scan
    ports = [21, 22, 23, 25, 53, 80, 110, 443, 8080]

    # Try to connect to each port
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)  # Timeout of 1 second
        result = sock.connect_ex((target, port))
        
        # Check if the port is open (result == 0 means open)
        if result == 0:
            print(f"Port {port} is open")
        else:
            print(f"Port {port} is closed")
        
        sock.close()

# Main Program
if __name__ == "__main__":
    target_ip = input("Enter target IP address: ")
    print(f"Scanning {target_ip}...")
    scan_ports(target_ip)
