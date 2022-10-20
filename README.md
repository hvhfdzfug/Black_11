# Black_11
if text == "تفعيل شخصيه" or text == "تفعيل شخصيتي" then
if not msg.Admin then
send(msg_chat_id,msg_id,'\n* ♡ هذا الامر يخص  '..Controller_Num(7)..' * ',"md",true)  
end
Redis:del(Fast.."shakse"..msg_chat_id)
send(msg_chat_id,msg_id,'\n* ♡ تم تفعيل امر شخصيتي * ',"md",true)  
end
if text == "تعطيل شخصيتي" or text == "تعطيل شخصيه" then
if not msg.Admin then
send(msg_chat_id,msg_id,'\n* ♡ هذا الامر يخص  '..Controller_Num(7)..' * ',"md",true)  
end
Redis:set(Fast.."shakse"..msg_chat_id,"off")
send(msg_chat_id,msg_id,'\n* ♡ تم تعطيل امر شخصيتي * ',"md",true)  
end


if (text == 'شخصيتي' or text == 'حدد شخصيتي' or text == 'حددي شخصيتي') and not Redis:get(Fast.."shakse"..msg_chat_id) then
local texting = {"عنيده", 
"متردده  ",
"خبيثة  ", 
"ايجابية ", 
"غامضة  ", 
"ضعيفة ", 
"كلاسيكية  ", 
"مسالمة  ", 
"حماسية ", 
"قيادية  ", 
"شكاك  ", 
"رومنسية  ",
"محفزة  ",
"متعاونة  ",
"اجتماعية  ",
"عصبية ",
"نرجسية  ",
"انطوائية  ",
"مظلومة  ",
} 
zezee = texting[math.random(#texting)]
local barlo = bot.getUser(msg.sender_id.user_id)
local photo = bot.getUserProfilePhotos(msg.sender_id.user_id)
local news = '✅ شخصيتك -> '..zezee
if photo.total_count > 0 then
data = {} 
data.inline_keyboard = {
{
{text =news,url = "https://t.me/"..barlo.username..""}, 
},
}
local msgg = msg.id/2097152/0.5
https.request("https://api.telegram.org/bot"..Token.."/sendphoto?chat_id=" .. msg.chat_id .. "&photo="..photo.photos[1].sizes[#photo.photos[1].sizes].photo.remote.id.."&photo=".. URL.escape(news).."&reply_to_message_id="..msgg.."&parse_mode=markdown&disable_web_page_preview=true&reply_markup="..JSON.encode(data))
end
end
