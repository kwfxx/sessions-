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
hash=['8f7527c332be697d77503ae9b8fbd6f0affc821aea1c63b629b20bb6cb736ac9','1eb2a4e0a5e85df1df8e8702753935d9ce379a79052387bbbce18430d3ffadeb','7e5dbb2013710273840a25179c3fa1e385457b7457c3942ed86a592627182835','21be8f906a15d50043152b0d698e00eb3b0931f5b10b47c27056c682101a85b5']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is :', h)
	   print('كس امك لو انك مسرب لو تحاول تستخدمها بدون اذن المطور')
	   print('ملاحضة لو انك مشترك وما مفعله عندك راسل المطور @FFNZZ ولو انك ما مشترك لا تشغلها اذا تحب جوالك')
	   r()
	   time.sleep(90)
