import socket
import threading

# Known ports and their services
services = {
    20: "FTP Data",
    21: "FTP (File Transfer)",
    22: "SSH – Remote Login",
    23: "Telnet – Remote Terminal",
    25: "SMTP – Email Sending",
    53: "DNS – Domain Lookup",
    80: "HTTP – Web Server",
    110: "POP3 – Email Receiving",
    143: "IMAP – Email Fetching",
    443: "HTTPS – Secure Web Server",
    3306: "MySQL Database",
    3389: "RDP – Remote Desktop",
    8080: "Proxy / Alternative HTTP"
}

def scan_port(ip, port):
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(0.1)

    try:
        s.connect((ip, port))
        service = services.get(port, "Unknown Service")
        print(f"Port {port} OPEN – {service}")
    except:
        pass
    finally:
        s.close()

def main():
    ip = input("Enter target IP: ")
    start = int(input("Start port: "))
    end = int(input("End port: "))

    print(f"\nScanning ports {start}-{end} on {ip}...\n")

    threads = []

    for port in range(start, end + 1):
        t = threading.Thread(target=scan_port, args=(ip, port))
        threads.append(t)
        t.start()

    for t in threads:
        t.join()

    print("\nScan Completed!")

main()
