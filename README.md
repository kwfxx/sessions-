import subprocess, hashlib
import time
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
hash = ['81941b565529ff09b45e7f9211a9114b774a4ba37c6ec5f6143e2c1fb89961e8','668990ef045226d5b647e94889ad6e914ebf2c9f9fdaff7001525b4a18cf5054','668990ef045226d5b647e94889ad6e914ebf2c9f9fdaff7001525b4a18cf5054','4c944f7d5cabdea0e1d0eb25ddd687e7a20e48707e492e99153186c1d19c10ad','c39d82a13c6e5d985f797cd5556b5c6e3436428b419a2570b3f58594da458727','19651ef9311e4de131bf29d3d6a2f1d6d4d4a772417ee1ec107ae8f9b6cc3d10','1c1be9d6a46d4ef12f4f1ffa0274efc513c88d30acb214a650ea584c0dad2f28','700f6bbf2f8c46bb0d059a3909196ba4c13decafec6bdaa632b47ea1b730dd9f','114f9eca0ad10dc542c0d12fb2aba5ed4855172c910823c1d4fefafc08bc16a1','807ae83d5ca22d4833928962ed65156c233955c324e257928ee083dcbcd0c959','d5a82fca417a52a348e5669cfeb672ab8641d0085b11d4ea939f5f722fd9d462']
if h in hash:
	print('good / هاتفك مصرح للدخول ')
	pass
else :
	while True:

		print('your code is :',h)
		time.sleep(5)
