# ip-
from browser_history import get_history
import socket

# گرفتن تاریخچه مرورگر
outputs = get_history()

# outputs.history یک لیست از (زمان, url) هست
history = outputs.histories

if history:
    last_url = history[-1][1]  # گرفتن آخرین URL
    print(f"آخرین  mn باز شده: {last_url}")
    
    # گرفتن دامنه از URL
    domain = last_url.split("//")[-1].split("/")[0]
    print(f"دامنه: {domain}")

    try:
        ip_address = socket.gethostbyname(domain)
        print(f"آی‌پی آدرس: {ip_address}")
    except socket.gaierror:
        print("نتوانستم آی‌پی را بگیرم!")
else:
    print("تاریخچه خالی است.")
