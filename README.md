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
hash=['8e177d4d82fa50f878397ee915f02e851491f7295460f83eee9450e3b0091ff5','294b6221ca2add3f64f9d583b20bce571fc61daf1acb85687b4d73342d1b6c53','f1f6fcc67d547a229c0956c9fc4a2e6d23247dc578ee4471fcaa5b1ac64b897c','daaeac2cd93a2b45eb71d4530a047016d2c7c135f361b930895fc9d8ebaf0265','6d04401681161cdf7ce10cef675c86e44084b65de5db0d4afb664e9ce523135b','bff1350461f9c29a8500875b1bbd87cdb7b608541fbdb9e04104033e016104ae','81941b565529ff09b45e7f9211a9114b774a4ba37c6ec5f6143e2c1fb89961e8','9e259ee9ab063f208a494e03aa8d23a343541165ded9b92dcb655c3e71127627','9b8f00e0e36b78821568aa4159f548333f00ce0f5c6ae618b7a87e0417ed49c6','0f9541560ac1a2bb629ee473c175a222818f306524f4ef8b4e4b2751a46eb021','e3d2f36dc41407c03068126ca33535180af8583b849c54a7bfddcff265f7f3ea','5492156e8956344a4cfd3ec430368d2d85a4c8fca36ce8a4ca7e2f30f6eb25b0','1eb2a4e0a5e85df1df8e8702753935d9ce379a79052387bbbce18430d3ffadeb','300018a7f9a6ff4d6938270b0bc2f24d2801d2b540e034f068634de0c6b62f61','156f63bd23ff7e694d2f12d4f4d086e8c01bf1da28ef4c0ef2967d135f4bcb21','53e39650f0f730d6848b183636ee1e6156ac4df4427879d7d358c67affd6ea41','a2b902827982c5e667eca5f2580cc99e6df7b7a4fbcf189b41978b1f78d3cac9','eeaed30664a309dc7b92c7a3d61b2b9fd6036dbb17984117b48543bb139c6aa5','8448df0e84a3baf0b58264bc1b538648e6e4d39ee9047645f6d687ad9d86c0d9','70d1489f3944356042da509d635772dfe92ea50fe94b609c1f584e5f28a2f022','21be8f906a15d50043152b0d698e00eb3b0931f5b10b47c27056c682101a85b5','c39d82a13c6e5d985f797cd5556b5c6e3436428b419a2570b3f58594da458727','9cf078cb0adcf967163357c07fe785223b17ab1c8783eebaa6ba1c62a61f510c','22c774cafc84765480eeabf68cff63ea5de7bf9a08c630a80e8ac8bcea77d971','572f56f0513492911e83f8fdfaf0e5d6a768a1ec465a757f9ae22760aae84eed','641427704b311baafb1888f5f9f5c649359e18917c57e3b860e55213a93348e4','86c0a12269b0a977bfb9fba9d46df57aca17fe6269c93c10e237a4337ddf7951']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is /', h)
	   print()
	   print('ملاحضة لو انك مشترك وما مفعله عندك راسل المطور @FFNZZ ولو انك ما مشترك لا تشغلها اذا تحب جوالك')
	   time.sleep(90)
