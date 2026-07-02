# eMAPT

**eLearnSecurity Mobile Application Penetration Tester** — covers Android and iOS penetration testing, from static analysis to runtime manipulation.

## Exam Format

- **Duration:** 7 days
- **Format:** Exploit a vulnerable Android application
- **Deliverable:** Working exploit + report

## Syllabus

| Domain | Topics |
|--------|--------|
| Android Architecture | APK structure, Dalvik/ART, permissions, intents |
| Static Analysis | Decompile APK, review AndroidManifest.xml, find hardcoded secrets |
| Dynamic Analysis | Frida, Objection, runtime hooking, SSL pinning bypass |
| Network Traffic | MitM with Burp on device, certificate installation |
| Vulnerabilities | Exported activities, deep links, insecure storage, content providers |
| iOS Architecture | IPA structure, Keychain, plist analysis |
| iOS Dynamic | Frida on jailbroken device, Cycript, runtime patching |

## Android Quick Reference

```bash
# Decompile APK
apktool d app.apk
jadx -d output/ app.apk

# ADB commands
adb devices
adb shell
adb logcat | grep -i password

# Frida SSL pinning bypass
frida -U -f com.target.app -l ssl-pinning-bypass.js --no-pause

# Objection
objection -g com.target.app explore
android sslpinning disable
android root disable
```

## Tools

`apktool` `jadx` `frida` `objection` `burpsuite` `adb` `MobSF` `drozer`
