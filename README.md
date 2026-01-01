from instagrapi import Client
import time

# আপনার ইনস্টাগ্রাম ইউজারনেম এবং পাসওয়ার্ড
USERNAME = 'your_username'
PASSWORD = 'your_password'

cl = Client()
cl.login(USERNAME, PASSWORD)

# যে গ্রুপে (Thread) বট কাজ করবে তার ID
# এটি পেতে cl.direct_threads() ব্যবহার করতে পারেন
thread_id = 'your_group_thread_id'

while True:
    try:
        # গ্রুপ নেম চেঞ্জ করা
        new_name = "Bot Group " + str(time.time())
        cl.direct_thread_rename(thread_id, new_name)
        print(f"Group name changed to: {new_name}")

        # মেসেজ পাঠানো
        cl.direct_answer(thread_id, "This is an automated message!")
        print("Message sent!")

        # অল্প বিরতি দিন যাতে ইনস্টাগ্রাম আপনাকে ব্লক না করে
        time.sleep(30) 
    except Exception as e:
        print(f"Error: {e}")
        time.sleep(60)
