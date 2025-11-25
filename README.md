local HttpService = game:GetService("HttpService")

local WEBHOOK = "https://canary.discord.com/api/webhooks/1442925860498833572/bWpU0pZpta2XTzAdIxG4ARhyKclVvQ49-BS2F1ioB3ycsvcEkmlNCK51ujJ3iXRQSeqX"

local function sendNotification()
    local data = {
        content = "@everyone O script foi executado!",
        embeds = {{
            title = "🟢 Script Executado",
            color = 0x00FF00,
            fields = {
                { name = "Horário", value = os.date("%Y-%m-%d %H:%M:%S"), inline = true },
                { name = "Status", value = "Executado com sucesso.", inline = true }
            }
        }}
    }

    pcall(function()
        HttpService:RequestAsync({
            Url = WEBHOOK,
            Method = "POST",
            Headers = { ["Content-Type"] = "application/json" },
            Body = HttpService:JSONEncode(data)
        })
    end)
end

sendNotification()
