###deploy to heroku###
[![Deploy](https://telegra.ph/file/aaa10262ebe6670eecf58.jpg)](https://heroku.com/deploy?template=https://github.com/chathush999/VCPlayBot.git)



import os
import io
import requests
from io import BytesIO
import re
from requests import get
from pyrogram.types import Message
from wbb import app as pbot
from bs4 import *
from pyrogram import filters  
from PIL import Image
from pyrogram.types import InlineKeyboardMarkup, InlineKeyboardButton


@pbot.on_message(filters.command("logo"))
async def make_logo(_, message):
    imgcaption = f"""
☘️ Logo Created Successfully
◇───────────────◇
🔥 Created by : @Devid999_bot
🌷 Requestor : {message.from_user.mention}
⚡️ Powered By   : @devid_support_gruop
◇───────────────◇
"""
    if len(message.command) < 2:
            return await message.reply_text("Please give a text to make logo 📸")
    m = await message.reply_text("📸 Creating..")
    text = message.text.split(None, 1)[1]
    photo = get(f"https://api.single-developers.software/logohq?name={text}").history[1].url
    await m.edit("📤 Uploading ...")
    await pbot.send_photo(message.chat.id, photo=photo, caption=imgcaption.format(message.from_user.mention),
                 reply_markup=InlineKeyboardMarkup(
            [
                [
                    InlineKeyboardButton(
                        "••Telegraph Link••", url=f"{photo}"
                    )
                ]
            ]
          ),
    )
    await m.delete()
            
            
@pbot.on_message(filters.command("write"))
async def make_logo(_, message):
    imgcaption = f"""
☘️write Successfully
◇───────────────◇
🔥 Created by : @Devid999_bot
🌷 Requestor : {message.from_user.mention}
⚡️ Powered By   : @devid_support_gruo
◇───────────────◇
"""
    if len(message.command) < 2:
            return await message.reply_text("Please give a text to write ✍️")
    m = await message.reply_text("✍️ writeing ..")
    text = message.text.split(None, 1)[1]
    photo = get(f"https://api.single-developers.software?write={text}").history[1].url
    await m.edit("📤 Uploading ...")
    await pbot.send_photo(message.chat.id, photo=photo, caption=imgcaption.format(message.from_user.mention),
                 reply_markup=InlineKeyboardMarkup(
            [
                [
                    InlineKeyboardButton(
                        "••Telegraph Link••", url=f"{photo}"
                    )
                ]
            ]
          ),
    )
    await m.delete()

@pbot.on_message(filters.command("glogo"))
async def make_logo(_, message):
    imgcaption = f"""
☘️ Logo Created Successfully
◇───────────────◇
🔥 Created by : @Devid999_bot
🌷 Requestor : {message.from_user.mention}
⚡️ Powered By   : @devid_support_gruo
◇───────────────◇
"""
    if len(message.command) < 2:
            return await message.reply_text("Please provide a name... 📸")
    m = await message.reply_text("📸 making your logo...")
    text = message.text.split(None, 1)[1]
    req = requests.get(f"https://sd-logo-api.herokuapp.com/?logo={text}")
    IMG = req.text
    await m.edit("📤 Uploading ...")
    await pbot.send_photo(message.chat.id, photo=IMG, caption=imgcaption.format(message.from_user.mention)),
    await m.delete()
