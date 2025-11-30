import subprocess, hashlib

def run(cmd):
    try:
        out = subprocess.check_output(cmd, shell=True, stderr=subprocess.DEVNULL)
        return out.decode().strip()
    except Exception:
        return ""

android_id = run("settings get secure android_id")
serial = run("getprop ro.serialno") or run("getprop ro.boot.serialno") or run("getprop ro.hardware")
brand = run("getprop ro.product.brand")
model = run("getprop ro.product.model")
mac = run("cat /sys/class/net/wlan0/address 2>/dev/null")
values = [v for v in [android_id, serial, brand, model, mac] if v]
concat = "|".join(values)

SALT = "سِرّ_خاص_قوي_غير_مُشارَك"

full = SALT + "|" + concat
h = hashlib.sha256(full.encode()).hexdigest()
hash = ['81941b565529ff09b45e7f9211a9114b774a4ba37c6ec5f6143e2c1fb89961e8','668990ef045226d5b647e94889ad6e914ebf2c9f9fdaff7001525b4a18cf5054','668990ef045226d5b647e94889ad6e914ebf2c9f9fdaff7001525b4a18cf5054','4c944f7d5cabdea0e1d0eb25ddd687e7a20e48707e492e99153186c1d19c10ad']
if h in hash:
	print('good / هاتفك مصرح للدخول ')
	pass
else :
	while True:
		print('your code is :',h)
	

