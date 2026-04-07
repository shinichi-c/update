# 1. What was added to the UpdateChecker.kt file:

1 - Cache Buster (?t=...): GitHub saves a "cached" version of your file for 5 minutes. If you update your JSON and then immediately open your app, the app will see the old version. I added a timestamp to the URL so GitHub is forced to give you the newest version every time.

2 - Detailed Logcat Tags: I simplified all the logs to use the single tag UpdateCheck so your Termux command su -c "logcat | grep UpdateCheck" works perfectly.

3 - Error Toasts: I added Toast.makeText. If your JSON is broken again in the future, the app will now pop up a message saying "Unexpected JSON token..." or "Connection Timeout," so you don't have to guess why it's not working.

4 -Robust Version Stripping: The logic now takes 4.2-FireFlies, splits it at the -, and only compares the 4.2. This prevents "FireFlies" from confusing the math.

# 2. Test with the Python command in Termux.

python3 -m json.tool update.json

# 3. A new updater-2.0 Format

{
  "latestVersion": "4.2-FireFlies",
  "downloadUrl": "YOUR_LINK_HERE",
  "changelog": "🚀 NEW FEATURES:\n- Added 3D Engine\n- Improved \"3D Pop\" logic\n\n⚡ PERFORMANCE:\n- Faster loading\n- Lower memory usage\n\n🛠️ BUG FIXES:\n- Fixed crash on start"
}
