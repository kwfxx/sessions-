import subprocess
import hashlib
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
hash=['8e177d4d82fa50f878397ee915f02e851491f7295460f83eee9450e3b0091ff5','294b6221ca2add3f64f9d583b20bce571fc61daf1acb85687b4d73342d1b6c53','f1f6fcc67d547a229c0956c9fc4a2e6d23247dc578ee4471fcaa5b1ac64b897c','daaeac2cd93a2b45eb71d4530a047016d2c7c135f361b930895fc9d8ebaf0265','6d04401681161cdf7ce10cef675c86e44084b65de5db0d4afb664e9ce523135b','bff1350461f9c29a8500875b1bbd87cdb7b608541fbdb9e04104033e016104ae']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is /', h)
	   print()
	   print('ملاحضة لو انك مشترك وما مفعله عندك راسل المطور @FFNZZ ولو انك ما مشترك لا تشغلها اذا تحب جوالك')
	   time.sleep(90)
