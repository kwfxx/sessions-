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
hash = ['خلي الهاش الي يطلعلك هنا']
if h in hash:
	print('good / هاتفك مصرح للدخول ')
	pass
else :
	while True:
		print('your code is :',h)
	
'6bf28abdc354288b73bf99008f6a361f',
'df7246019b382003c7d438e2eec3f812',
'f4fd0301c875e5a5da06c14fd136934c',
'20f03a3785cbab1d1f242c50a8b2ef21',
'93bf67de66b6ddff3a75c3aec78e7276',
'0428ad14102a079e02df973ef9c3ca34',
'a7a6042fd8bb7aa59496346d9646e46f',
'525d663adcec79b1601cdfa2125627dc',
'8100a904b508f86fa19c3b3a2146a979',
'd972be2b916d7cb7a3e2c534dac73439',
'30c2b94bf3ddd98952a6f28137250375',
'fd4cd15633d1ebceccc492d509a9522b',
'648c1df7cef3ed3bd814c932939ce846',
'0f2d6256d2252a5cecd575b76009e8c2',
'bb4cef9ef619cb46f0a45c308c0d1e25',
'278b94bbb57a92ff23d92c5c52e1d57e',
'59317ae149b292fa766df9b805d4012e',
'40035d852d85c40b180d5154dce74e32',
'572670e81c97c6b16e081ee0243883b5',
'8a53b9f0b2ad46141f3ef206170ea95f',
'e54ae478d3928c1980661d3dcc81127e',
'cec657d01305d24d62ead1ebca1ea0de',
'1aa7da779bfb34e9adcda9d330242347',
'0727771a119768c35ddad138ae669ccb',
'b394eaa0f2376832f1e65701406872b4',
'1fc1c3d992d806afbb88fb05b3f8b51b',
'56e02966f4761a361a575db0a32ba2f7',
'978573dbd8fb062130305da932016754',
'466efa18c526a080549b97f03305a3a9',
'1f7b16535d0c8f91d1b0f0d4291726c7',
'c5a5d59db6c74831c598bbacee8ad25a',
'2b052a3a01222be0da70fd2849f6f849',
'18c9b9a235c938b34c1f8c5af3c65eb3',
'847ce0bac8342d7e63798419c0958268',
'08d0463c3ea0a3c7ef8f6a8e2e341528',
'138b138be22630bb46a0dd4d747dc037',
'6f8fd20e4cfb6af8d68e38284f732269',
'266d4adf7a9741e20386d77215fe1e1c',
'f76100b0c36e12ceec7dfedebb50f967'
            ])

      
cookies ={
            "passport_csrf_token": self.secret,
            "passport_csrf_token_default": self.secret,
            "sessionid": ksks
            }
self.ses.cookies.update(cookies)
