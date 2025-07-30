# expert-broccoli// الخطة فاشوش - نسخة أولية // الواجهة بلغة React + دعم عربي وإنجليزي + إعدادات إنشاء الروم

import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input"; import { Switch } from "@/components/ui/switch";

export default function CreateRoom() { const [roomName, setRoomName] = useState(""); const [isPrivate, setIsPrivate] = useState(false); const [withPassword, setWithPassword] = useState(false); const [password, setPassword] = useState(""); const [maxPlayers, setMaxPlayers] = useState(4); const [language, setLanguage] = useState("ar"); const [withBots, setWithBots] = useState(false); const [numBots, setNumBots] = useState(1);

return ( <div className="min-h-screen bg-gray-100 flex items-center justify-center p-4"> <Card className="w-full max-w-md"> <CardContent className="space-y-4"> <h1 className="text-2xl font-bold text-center"> {language === "ar" ? "إنشاء روم جديد" : "Create New Room"} </h1>

<Input
        placeholder={language === "ar" ? "اسم الروم" : "Room Name"}
        value={roomName}
        onChange={(e) => setRoomName(e.target.value)}
      />

      <div className="flex items-center justify-between">
        <label>{language === "ar" ? "روم خاص" : "Private Room"}</label>
        <Switch checked={isPrivate} onCheckedChange={setIsPrivate} />
      </div>

      <div className="flex items-center justify-between">
        <label>{language === "ar" ? "كلمة مرور" : "With Password"}</label>
        <Switch checked={withPassword} onCheckedChange={setWithPassword} />
      </div>

      {withPassword && (
        <Input
          placeholder={language === "ar" ? "كلمة المرور" : "Password"}
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
      )}

      <div className="flex items-center justify-between">
        <label>{language === "ar" ? "عدد اللاعبين" : "Max Players"}</label>
        <Input
          type="number"
          value={maxPlayers}
          min={2}
          max={16}
          onChange={(e) => setMaxPlayers(e.target.value)}
        />
      </div>

      <div className="flex items-center justify-between">
        <label>{language === "ar" ? "إضافة بوتات" : "Add Bots"}</label>
        <Switch checked={withBots} onCheckedChange={setWithBots} />
      </div>

      {withBots && (
        <Input
          type="number"
          value={numBots}
          min={1}
          max={5}
          onChange={(e) => setNumBots(e.target.value)}
        />
      )}

      <div className="flex items-center justify-between">
        <label>{language === "ar" ? "اللغة" : "Language"}</label>
        <select
          className="border rounded p-2"
          value={language}
          onChange={(e) => setLanguage(e.target.value)}
        >
          <option value="ar">العربية</option>
          <option value="en">English</option>
        </select>
      </div>

      <Button className="w-full">
        {language === "ar" ? "ابدأ اللعبة" : "Start Game"}
      </Button>
    </CardContent>
  </Card>
</div>

); }

