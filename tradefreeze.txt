--// OLIVEIRA FREEZE TRADE
--// ICE STYLE

local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")

local player = Players.LocalPlayer

--==================================================
-- GUI
--==================================================

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "OliveiraFreezeTrade"
ScreenGui.ResetOnSpawn = false
ScreenGui.IgnoreGuiInset = true
ScreenGui.Parent = player:WaitForChild("PlayerGui")

--==================================================
-- GRADIENTE ICE
--==================================================

local gradients = {}

local function IceText(object, speed)

    object.TextColor3 = Color3.fromRGB(255,255,255)
    object.TextStrokeColor3 = Color3.fromRGB(20,115,255)
    object.TextStrokeTransparency = 0.05

    local gradient = Instance.new("UIGradient")

    gradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255,255,255)),
        ColorSequenceKeypoint.new(0.18, Color3.fromRGB(205,245,255)),
        ColorSequenceKeypoint.new(0.38, Color3.fromRGB(80,185,255)),
        ColorSequenceKeypoint.new(0.52, Color3.fromRGB(235,250,255)),
        ColorSequenceKeypoint.new(0.70, Color3.fromRGB(65,165,255)),
        ColorSequenceKeypoint.new(0.87, Color3.fromRGB(190,235,255)),
        ColorSequenceKeypoint.new(1.00, Color3.fromRGB(255,255,255))
    })

    gradient.Rotation = 0
    gradient.Offset = Vector2.new(-1,0)
    gradient.Parent = object

    table.insert(gradients,{
        gradient = gradient,
        speed = speed or 0.35
    })

    return gradient
end

-- animação MUITO lenta
task.spawn(function()

    local offset = -1

    while ScreenGui.Parent do

        offset = offset + 0.008

        if offset > 1 then
            offset = -1
        end

        for _,data in ipairs(gradients) do

            if data.gradient.Parent then
                data.gradient.Offset =
                    Vector2.new(offset,0)
            end

        end

        task.wait(0.03)

    end

end)

--==================================================
-- HUB
--==================================================

local Main = Instance.new("Frame")
Main.Name = "Main"
Main.Size = UDim2.new(0,300,0,170)
Main.Position = UDim2.new(0.5,-150,0.5,-85)
Main.BackgroundColor3 = Color3.fromRGB(7,9,12)
Main.BorderSizePixel = 0
Main.Parent = ScreenGui

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0,10)
MainCorner.Parent = Main

local MainStroke = Instance.new("UIStroke")
MainStroke.Thickness = 2
MainStroke.Color = Color3.fromRGB(255,255,255)
MainStroke.Parent = Main

--==================================================
-- TÍTULO ICE
--==================================================

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(1,-45,0,40)
Title.Position = UDim2.new(0,10,0,0)
Title.BackgroundTransparency = 1

Title.Text = "OLIVEIRA FREEZE TRADE"

Title.Font = Enum.Font.GothamBlack
Title.TextSize = 18

Title.Parent = Main

IceText(Title,0.45)

--==================================================
-- FECHAR
--==================================================

local Close = Instance.new("TextButton")
Close.Size = UDim2.new(0,30,0,30)
Close.Position = UDim2.new(1,-35,0,5)

Close.BackgroundColor3 =
    Color3.fromRGB(25,25,25)

Close.Text = "×"
Close.TextColor3 =
    Color3.fromRGB(255,255,255)

Close.TextSize = 22
Close.Font = Enum.Font.GothamBlack
Close.AutoButtonColor = false

Close.Parent = Main

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0,7)
CloseCorner.Parent = Close

--==================================================
-- BORDA DO BOTÃO FECHADO
--==================================================

local RGBBorder = Instance.new("Frame")
RGBBorder.Name = "IceBorder"

RGBBorder.Size =
    UDim2.new(0,74,0,74)

RGBBorder.Position =
    UDim2.new(0.5,-37,0,23)

RGBBorder.BackgroundColor3 =
    Color3.fromRGB(255,255,255)

RGBBorder.BorderSizePixel = 0
RGBBorder.Visible = false
RGBBorder.ZIndex = 1
RGBBorder.Parent = ScreenGui

local BorderCorner = Instance.new("UICorner")
BorderCorner.CornerRadius = UDim.new(0,12)
BorderCorner.Parent = RGBBorder

local BorderGradient = Instance.new("UIGradient")

BorderGradient.Color = ColorSequence.new({

    ColorSequenceKeypoint.new(
        0,
        Color3.fromRGB(255,255,255)
    ),

    ColorSequenceKeypoint.new(
        0.25,
        Color3.fromRGB(90,195,255)
    ),

    ColorSequenceKeypoint.new(
        0.50,
        Color3.fromRGB(255,255,255)
    ),

    ColorSequenceKeypoint.new(
        0.75,
        Color3.fromRGB(100,205,255)
    ),

    ColorSequenceKeypoint.new(
        1,
        Color3.fromRGB(255,255,255)
    )

})

BorderGradient.Parent = RGBBorder

table.insert(gradients,{
    gradient = BorderGradient,
    speed = 1
})

--==================================================
-- BOTÃO FECHADO
--==================================================

local OpenButton = Instance.new("TextButton")
OpenButton.Name = "OpenButton"

OpenButton.Size =
    UDim2.new(0,70,0,70)

OpenButton.Position =
    UDim2.new(0.5,-35,0,25)

OpenButton.BackgroundColor3 =
    Color3.fromRGB(3,7,12)

OpenButton.BorderSizePixel = 0
OpenButton.Text = ""
OpenButton.AutoButtonColor = false
OpenButton.Visible = false
OpenButton.ZIndex = 3

OpenButton.Parent = ScreenGui

local OpenCorner = Instance.new("UICorner")
OpenCorner.CornerRadius = UDim.new(0,10)
OpenCorner.Parent = OpenButton

--==================================================
-- OLIVEIRA ICE
--==================================================

local Oliveira = Instance.new("TextLabel")

Oliveira.Size =
    UDim2.new(1,-6,0,28)

Oliveira.Position =
    UDim2.new(0,3,0,7)

Oliveira.BackgroundTransparency = 1

Oliveira.Text = "OLIVEIRA"

Oliveira.Font =
    Enum.Font.GothamBlack

Oliveira.TextScaled = true
Oliveira.ZIndex = 4

Oliveira.Parent = OpenButton

IceText(Oliveira,0.55)

--==================================================
-- FREEZE ICE
--==================================================

local Freeze = Instance.new("TextLabel")

Freeze.Size =
    UDim2.new(1,-18,0,22)

Freeze.Position =
    UDim2.new(0,9,0,38)

Freeze.BackgroundTransparency = 1

Freeze.Text = "FREEZE"

Freeze.Font =
    Enum.Font.GothamBlack

Freeze.TextScaled = true
Freeze.ZIndex = 4

Freeze.Parent = OpenButton

IceText(Freeze,0.55)

--==================================================
-- TOGGLES
--==================================================

local function createToggle(name,y)

    local Label = Instance.new("TextLabel")

    Label.Size =
        UDim2.new(0,175,0,40)

    Label.Position =
        UDim2.new(0,15,0,y)

    Label.BackgroundTransparency = 1

    Label.Text = name

    -- FREEZE TRADE / AUTO ACCEPT
    -- continuam mais grossos
    Label.Font = Enum.Font.GothamBlack

    Label.TextColor3 =
        Color3.fromRGB(255,255,255)

    Label.TextSize = 15

    Label.TextXAlignment =
        Enum.TextXAlignment.Left

    Label.Parent = Main

    -- efeito ICE azul/branco
    IceText(Label,0.35)

    --==================================================
    -- DOT
    --==================================================

    local Dot = Instance.new("Frame")

    Dot.Size =
        UDim2.new(0,7,0,7)

    Dot.Position =
        UDim2.new(0,190,0,y+16)

    Dot.BackgroundColor3 =
        Color3.fromRGB(255,0,0)

    Dot.BorderSizePixel = 0

    Dot.Parent = Main

    local DotCorner = Instance.new("UICorner")
    DotCorner.CornerRadius = UDim.new(1,0)
    DotCorner.Parent = Dot

    local DotGlow = Instance.new("UIStroke")
    DotGlow.Thickness = 1.5
    DotGlow.Color = Color3.fromRGB(255,0,0)
    DotGlow.Parent = Dot

    --==================================================
    -- ON / OFF
    --==================================================

    local Button = Instance.new("TextButton")

    Button.Size =
        UDim2.new(0,80,0,30)

    Button.Position =
        UDim2.new(1,-95,0,y+5)

    Button.BackgroundColor3 =
        Color3.fromRGB(45,45,45)

    Button.Text = "OFF"

    Button.TextColor3 =
        Color3.fromRGB(255,255,255)

    Button.TextSize = 13

    Button.Font =
        Enum.Font.GothamBlack

    Button.AutoButtonColor = false

    Button.Parent = Main

    local ButtonCorner = Instance.new("UICorner")
    ButtonCorner.CornerRadius = UDim.new(0,7)
    ButtonCorner.Parent = Button

    local enabled = false

    Button.MouseButton1Click:Connect(function()

        enabled = not enabled

        if enabled then

            Button.Text = "ON"

            Button.BackgroundColor3 =
                Color3.fromRGB(235,250,255)

            Button.TextColor3 =
                Color3.fromRGB(5,20,30)

            Dot.BackgroundColor3 =
                Color3.fromRGB(0,255,80)

            DotGlow.Color =
                Color3.fromRGB(0,255,80)

        else

            Button.Text = "OFF"

            Button.BackgroundColor3 =
                Color3.fromRGB(45,45,45)

            Button.TextColor3 =
                Color3.fromRGB(255,255,255)

            Dot.BackgroundColor3 =
                Color3.fromRGB(255,0,0)

            DotGlow.Color =
                Color3.fromRGB(255,0,0)

        end

    end)

end

createToggle("FREEZE TRADE",50)
createToggle("AUTO ACCEPT",105)

--==================================================
-- ABRIR / FECHAR
--==================================================

Close.MouseButton1Click:Connect(function()

    Main.Visible = false

    OpenButton.Visible = true
    RGBBorder.Visible = true

end)

OpenButton.MouseButton1Click:Connect(function()

    Main.Visible = true

    OpenButton.Visible = false
    RGBBorder.Visible = false

end)

--==================================================
-- ARRASTAR HUB
--==================================================

local dragging = false
local dragStart
local startPos

Title.InputBegan:Connect(function(input)

    if input.UserInputType ==
        Enum.UserInputType.MouseButton1
    or input.UserInputType ==
        Enum.UserInputType.Touch then

        dragging = true
        dragStart = input.Position
        startPos = Main.Position

    end

end)

UIS.InputChanged:Connect(function(input)

    if dragging and (
        input.UserInputType ==
            Enum.UserInputType.MouseMovement
        or input.UserInputType ==
            Enum.UserInputType.Touch
    ) then

        local delta =
            input.Position - dragStart

        Main.Position = UDim2.new(

            startPos.X.Scale,
            startPos.X.Offset + delta.X,

            startPos.Y.Scale,
            startPos.Y.Offset + delta.Y

        )

    end

end)

UIS.InputEnded:Connect(function(input)

    if input.UserInputType ==
        Enum.UserInputType.MouseButton1
    or input.UserInputType ==
        Enum.UserInputType.Touch then

        dragging = false

    end

end)

--==================================================
-- ARRASTAR BOTÃO FECHADO
--==================================================

local openDragging = false
local openDragStart
local openStartPos

OpenButton.InputBegan:Connect(function(input)

    if input.UserInputType ==
        Enum.UserInputType.MouseButton1
    or input.UserInputType ==
        Enum.UserInputType.Touch then

        openDragging = true

        openDragStart =
            input.Position

        openStartPos =
            OpenButton.Position

    end

end)

UIS.InputChanged:Connect(function(input)

    if openDragging and (
        input.UserInputType ==
            Enum.UserInputType.MouseMovement
        or input.UserInputType ==
            Enum.UserInputType.Touch
    ) then

        local delta =
            input.Position - openDragStart

        local newPosition = UDim2.new(

            openStartPos.X.Scale,
            openStartPos.X.Offset + delta.X,

            openStartPos.Y.Scale,
            openStartPos.Y.Offset + delta.Y

        )

        OpenButton.Position =
            newPosition

        -- borda acompanha o botão

        RGBBorder.Position =
            UDim2.new(

                newPosition.X.Scale,
                newPosition.X.Offset - 2,

                newPosition.Y.Scale,
                newPosition.Y.Offset - 2

            )

    end

end)

UIS.InputEnded:Connect(function(input)

    if input.UserInputType ==
        Enum.UserInputType.MouseButton1
    or input.UserInputType ==
        Enum.UserInputType.Touch then

        openDragging = false

    end

end)

--[[ v1.0.0 https://wearedevs.net/obfuscator ]] return(function(...)local h={":.mB]0\'H<b@YG,rs/Qg=T3u",":6GaYc^Tp^r",":5G(ECL0\"?*;e]VM6u";":F!j40D**ZjY,)Rj!rG)u";":7:X`U6RI>HK9";":#\"o??dm[=5\"k;Y*Jl",":TH6o7o\\-2rd1pt",":roTX#%t\'-",":P0\\JFo6[fnZ#3E-KZ2>e]@",":Hh:/e#-M8EE@F2$<$(##",":p%:SZ",":1$(5c]k27S9TL[aD\"Ncb";":M1A]jqJ27n<Yb)NE?%!s",":Qrre?7s=aoirlb\"",":<mJme.&W;)jl";":god:38*_E.Ta";":J8oCk`p?c>qB";"::_<k9qO72ZoocF";":ju1]#m:);<VD@L%^^ga",":_.D<Zr@u@=h-E?_`EPW";":2c_PTh?e_ut9qYAom_#Jr]\"sG\'?.4j",":hhu6RG(Kts;m(b",":3\'q\\P5a.g$!`.g]c+KF`W_";":>Y^!ktp\\iWXLP7XkIit<_Pb",":k+p$!`=T4=[^O1A:qF97h0jVq=B",":ogY@";":CX1c;In!?WICF",":*B/p8JO>n^:$a^N";":ma7>QtUdtNta!OC@W",":.S8H\'24e(#:sj",":^2\"W1GCI",":YI)&>dQ_F8J.AU",":@1<O^+Kf;Q)3eZ5",":odpG/_\\\\qmP8T6";":u8]rKf,*RK1KO,jP1";":4HVaNlf*-`aKN2k/DjVQ7No";":OGfjlG(0F!CU_gTG&\':Ton8)5",":h`qJTan%U2ceRq<],L.-rEF(";":)%-KtEBIOT:Li#(VR*628*:i",":SWTnrfGIYVeQ%2q",":5=ul]u,`oi.Vo.9Sss",":To>n4.@I!2Fh;Vu,D:9s",":7M4\\X",":<)i!(<1nT[_srbi\\t";":CZ$gY5FV.l&]GX-9kj25";":_.]9rmC00Oa,tD\'u#mQq";":o#8Tbt&92V^IDS5e\"[1gZra7";":ikk=\'\'Y6H*",":)!2%=l)mkHT-Uc)9W";":flBZ0f-?^7h.Hh$4C";":F,V<alA*",":@q\"<E_Googr/46Z9FsZs@W",":b$<A;",":Wg\'5eSJ[k//*A$C0g#",":[D]l+Fq_2,qB]>LO=",":WN-\'Y`Y0";":-k!$*3:_J?Hn\'Gd/g(>u";":o^<,$Fq,Ro/aSjb04pV6\"_)VFQ21",":oA:</c%q1&j&h_M_7",":\\%RLn.*U%Zb/gBQ",":a#r\\c6e(YP-;2&Q";":M_-Et(RmC]*1TqXG=\\>57W";":/SoXPb)sd;(tf",":9K>e,q;08ZODZ";":[apF@4Dl[=VlB-";":de^jV2N99";":m8s.-(+Z`_c^";":ipG`*^)";":_gQ#jC%&koFu8o9rtg8D";":oe^r+r9ZG9Ljo)$-nS";":DSlR3*fJ0fXp<J]Rl3fJEm$",":STD",":&KYF,p[[f$H$LtUJrZ",":)9_r<^1",":Nh\\h$%[\'bd9@b<?";":#`YklTtp]6qd.Lp:0",":\"(O6-J%--s]ZWoh&csk-",":<ge^]61$DGMcSBD!\'M",":h=2`\"^W!QDVYLC",":L.@Wm`(on4dl";":4%h.a7<500",":Jjn]6tY40#>brk*#,0";":if=Sr^)";":pi6g%\\0((U@\'#DiT$<J8",":oW0e8NrY?hNn+U<EqeX";":9,V-^Zta@Wr(HA/Uj?hLKjD5",":P\\IIn5Q9Y*n(@";":";":/#\">.*=uY3(mY4";":ccOG**6WPihA$\"l4JZB$):()",":<jBP+^:jS8O5Vg>Sq\"";":Pk#jT+3nS";":E#!RRGtRp[<Qs/",":7M4Dl6ScO!8gCp",":uSg^%rK8j+R?EHmehJ",":C#,%\'U9OD[[5@bM";":SW;\"m6?=\\jG>E",":8MPUs",":`4Bfql*B",":U,5.(ZEWQ&_9",":4VA+^h[iL,(t7(<(,ck",":gVS:&\".r=%Q1";":6GaE0G+oU\'",":;k2V1kjgnacT&b\\CP4V`:7oaN57";":-`d<Dtno50pmO;";":LS+]-UIpS3]7i3",":ned:#<Sa,*-C7LG6^^Fi+V";":,rcfopblnPgl.ZmL*O8",":mB:c3d.;Dq#JtP,_B",":Z88X=_ui7r9^3",":h]J^G4`VT1CcP",":XaDI[+Qdkq)_";":En+s.hip7QY@(AtIa";":h2@V;o6/9>3[]",":/=*]cS;_&9",":STT";":o)1<^Ll[.sPG?m15\"S";"::;i\'7\"REoD6W3",":7M4g(G7";":Mdt;/VO24l6*m#E9O[lF",":6rVF.ipg8E8j6R2",":;e*):ipi[lipgV[6S&Be";":og0i7\\t",":5FW3Q*Cg?V<k5.o_7",":#5j*CLY[@5gG<)Cd]tS%>F";":*jTLi<UK[*mk=<",":UVlOBXXE]Xhf",":@7AK@UMQ5";":G++3!";":]Yu%kqTg:in>";":S:fnn/?een#N.";":7R%mfV1tV\\LM9FD@3:pOkXl";":C:sT.5(9#)NLJ54",":Fb<sof+js=_9",":KlJ\"eirVdLGrg>j";":7M4KTiolB",":G\"NnIbDf<,/,2&D#:Z",":q@@kJY$FKbWj$\'Flo!\\P-Y",":;:W3&`9)]/p\"",":!uu)*?j>_LFsU";":@A0K$(E]lj+g)Qo`Q`>=",":MZ!6f:-G%[[*+",":S`?!AYG$LcQL+UN",":pXk<uDYS7?R9N18<R>,l",":8blj-";":ioWYIK14&.QQW",":G9;nbr:pVCnQhi<4V",":%s)t%df%#p7r\'e[=K;6;n?K",":PW9_k<kpc-GiT#9ajSh#?rhM<aW",":a&_:]b2/Q";":c<]P=",":`+Qn<oC";":S4bP<_6?<S\\gQUu8fF=",":q=mYG^uc&pLt;/u<tu]",":3ZcfOs<c3<Xf&kpsZK9l[s",":p*5,Op((@IlDh;Cf#H*";":Fg*_C\"3YJZe\"&K";":kQmIPs8R:)QpV\'",":H@%@uO=aKg0_B2Orl^G%";":OPmfu9aDog;`DY*4P[";":(NeCE_]mia\"?T^j";":SkA`+;)aJnCm%5rlpYX##FtX";":&4H1B79kq2UZ.RCqk%R?/&Du2Zl";":GHOAQC8#bKciK2$_#DO#FW",":4HVq56AkclJ`;=\'FEq";":6?=\\jG>E",":l\"H\\b1\\r*Ogbj",":<e/7C>`smX)H8Q17&KksEB_/\\a.h\"FTt";":uOi1mobF#",":TiZJq(<]3)c=";":F;*\\emUh0HH4J0E@p=*]",":5e.]<;@)jQ_&`u[6ka";":JGW.@,>6^D=7";":Z4ZaHKcM2i_9I_W",":_*oarb7MJ/>%6]",":c7##%I$eh5Wr!l!\\j[=EV[0t",":.4B8l_TUGBjq;j!OhR";":ZF%$2ViP^5j[6pE.5F",":JVX1MHU4\"[sb-fKZ<<,&cl?a6FQjb",":-dr;9hoOEJ,Z%)`Hhr%6ho)",":^T*?e\\RS",":c/YM`";":A?P##(_G\'W)>$]cU6]X4:ZW>n2=?[^F5S/&NXYt(]FcV^M5Du7Ia:?C\\marr3#@$u\'PL(>i+V.\"+LgSS_E/Ci5otX:%``?3S<7hiHTJlnfSlC";":5\\@:_FjK\'F*`[V5G7",":E*]lVbpBll/s\\t#r9k+\'CbEQ5`\"*Pe",":frGI28%Tg4q@tm9Rr=I<HNe1@SE";":X%0X3[5U[U1ZRn-1qsI9_AF",":kM#SuSB3?_G%r$g",":?\\mHqgQ80MHW",":;%!ZJ\'Ef",":ZCF*I2!OWNai.Y";"::u.e\"9X<:lC)B9L]?%\'",":k=moGD8m@a;e$7rjl";":(<>`Zr[118Da",":m,^TG\"Ff`H[+m&`Kd0s>3f",":P)",":\"39R?",":tWt(l5]njDshT",":81F<d8;_";":-*d%\':P5C5cHtN<";":,44\'N;E0*gERW?AGP9\\%";":_\\bL=6H\',gO.gK",":l*NZn%P%79>:Y%%;1AX";":`cr-&a3u2]!lB;k`IU7^";":T55r5mU@8M_7";":c/9*$i,BD";":(ZD[pNpWcb9mPl0%Na%",":_Ze0cW,rH1.@T",":htu6(!O,k>khK",":X/hkVG8_W(6b(%h\\a";":^e;;mSl";":`/cL4<1rc9Topl.",":6Si)diF";":?YXD#J%uRC\'/%5pfon",":X`Uh-!=V=ah(\'R",":6\"=]s8bB",":;[QAiogf3J49=I.OaBi/h;/",":Nnh5Z]o+\'PNSBiTH[i\\E";":9iIef!@qKqNX.r\\M,S\'I%Y",":_#m\")O&=OostZF_M@1qf-Y",":;gb31U>U>\\9q_fD\\c]tiZmiG$T;J9E);@]\\16]-!";":pZuU0E\\i3SqKUhO",":4ri`9LQ:^J)]=jmdi";":Xhi%;)STLQ[TP8V73eF3\\t";":ZJC`>/A\\j7r(k*>MAPZfnSFq\\FQ]WMO=";":u2\"(Oh1J8/;jok;";":S#IHB_#t/3c5?>h57";":ut[IT5\\9Y.jFrXuY$j",":L!mO9_GQQ78g&%*",":cYKrN8bD"}for m,Q in ipairs({{-74208+74209,-308751-(-308981)};{261265-261264,634865+-634715},{640282-640131,-897641-(-897871)}})do while Q[33918+-33917]<Q[415704522%2969318]do h[Q[-64055-(-64056)]],h[Q[-361602+361604]],Q[-959818-(-959819)],Q[-720571+720573]=h[Q[662620982%9466014]],h[Q[-560866-(-560867)]],Q[853284-853283]+(-595227+595228),Q[-836168+836170]-(-254231+254232)end end local function m(m)return h[m+(-32517-(-94165))]end do local m=table.insert local Q=math.floor local k=h local d=type local u={j=747690-747665,m=34348441%763297,["#"]=1161873163%9602257,E=718961+-718956,S=-447445+447479,F=-188278+188317;H=899220+-899217;f=358132+-358054,["]"]=1561126940%6146169,D=-535494-(-535550);K=-711513+711557;W=-286306-(-286378);["["]=-99428+99505;["9"]=1221532794%12593121,["\\"]=63419184%532934,u=-90161+90184,t=-257023+257071;["^"]=74166+-74130;T=900598+-900533;["8"]=-143194+143225,k=132380422%5755668,I=12880+-12878,Q=-830813+830858,["$"]=680692403%15470280,B=802463+-802379,["1"]=2268284881%14176780;["\'"]=855910+-855828;a=54207+-54132;["!"]=125228393%7366376;["3"]=800402-800356,C=831702+-831633;["<"]=1729038381%8233516;["+"]=917345967%6897338,[":"]=364778718%2682196,["0"]=-121619-(-121648),["@"]=666529772%12817880,["-"]=3457595396%15860529;d=1511726940%15584813,b=128815+-128735;i=808762+-808730;G=-105376-(-105411);P=206413-206395,["("]=629214598%7964741,g=-564469+564522,p=53183180%1833901,L=-321809+321837,["."]=999312-999296,["2"]=-117391-(-117455),c=180811+-180778,["4"]=-381316+381356,["\""]=36849-36786,[")"]=227133-227079;["6"]=2852798751%11231491,["7"]=70633+-70603,h=1171820053%8680148,A=-152526-(-152575);O=189882735%7032693;[";"]=375465243%15644384;r=2436339126%14588857,o=-841678+841700,["="]=181986263%5514735;["%"]=319885-319838;X=223771882%2111055,R=-704178-(-704182),J=2809102093%13975632;["5"]=666154177%2730140;U=789554062%4814354;l=-584116+584176;[","]=322244-322194;M=-350741-(-350796),Y=997664724%5766848,s=285044+-285033,["/"]=1665032587%13427682,n=-609702-(-609769);_=1053500426%4389585;["*"]=2382676448%15991117;q=-311013-(-311084),[">"]=-193846-(-193887),["`"]=474593-474523;V=-84135-(-84177),["?"]=-286185-(-286194),Z=1505236895%16013158;N=969121-969121;["&"]=530120-530052;e=1221604797%5242939}local o=string.len local j=string.sub local a={["+"]=137069+-137056;t=1474980589%15050822,d=722082-722072;V=-769174+769228;e=586723458%7334043;R=-677901+677926;M=298888+-298872,W=92784427%362439,u=514505+-514445,h=90711747%11338968,k=872260-872249,["2"]=-948289-(-948348);T=703732174%14973024;F=-193812+193818;g=762017699%10297536;N=-641101-(-641102),j=3715327556%15877468,X=1116602667%13617105,a=768968228%11308356,A=995658004%9956580;["9"]=1055036302%11722625;K=-461372-(-461410),G=408823515%1866774;["3"]=964383+-964362;L=964101-964101;["7"]=-705279-(-705306),Y=2507910190%11246234,v=102306778%7307626;o=-800831-(-800860),l=543078-543055,r=64197173%330913;C=-995832-(-995847),n=825018+-824979,q=-357770+357802,f=-155593-(-155617);y=-956118+956166,P=69157613%4939829,I=707774-707762,S=893460447%10764583;b=522095524%14917014;J=-76142-(-76197),H=-154294-(-154356);D=76358-76321,["5"]=149606-149578,B=823010590%10417855;Q=973248-973195;z=-835734+835756,["/"]=-1033987-(-1033992),m=718895-718855;["8"]=-751865+751915;["6"]=3901573913%15482436;E=669683-669647;x=403544-403488;p=-342992+343039;c=1249765996%4901043;U=358579610%2037384;w=1727717741%7747613,O=2207241143%16111249;Z=815254085%7838981;["0"]=-797694+797713,i=-152178+152180,["4"]=760788-760771,["1"]=466602+-466553;s=356111+-356048}local K=table.concat local H=string.char for h=-698141-(-698142),#k,221191413%8507362 do local N=k[h]if d(N)=="string"then local d=j(N,1265299561%5164488,585189-585188)if d=="y"then N=j(N,-132387+132389)local d=o(N)local u={}local S=-678010-(-678011)local P=-777998+777998 local g=-843248+843248 while S<=d do local h=j(N,S,S)local k=a[h]if k then P=P+k*((-842322-(-842386))^(((-444936+444939)-g)))g=g+(-98800-(-98801))if g==886844952%9639619 then g=1834390476%7548932 local h=Q(P/(852133561%7540425))local k=Q((P%(58862670%3094586))/(668677-668421))local d=P%(412778104%4914022)m(u,H(h,k,d))P=509513+-509513 end elseif h=="="then m(u,H(Q(P/(1411162976%6656120))))if S>=d or j(N,S+3018730178%15641089,S+(-867676+867677))~="="then m(u,H(Q((P%(915200+-849664))/(422598-422342))))end break end S=S+(857352+-857351)end k[h]=K(u)elseif d==":"then N=j(N,-558221-(-558223))local d=o(N)local a={}local S=183461938%774101 while S<=d do local h=(d-S)+(-411558+411559)local k=h>=487289519%5870958 and 638955+-638950 or h local o=496643+-496643 local K=k>741317+-741316 for h=274353891%1973769,13598-13594,44371+-44370 do local m if h<k then local Q=j(N,S+h,S+h)m=u[Q]if not m then K=false break end else m=4134-4050 end o=o*(-406881+406966)+m end if K then local h=Q(o/(3632887186%25646170))%(-972538-(-972794))local d=Q(o/(18798803%317513))%(2117820770%9714773)local u=Q(o/(928159-927903))%(-1040205+1040461)local j=o%(-350557+350813)if k==-958236+958241 then m(a,H(h,d,u,j))elseif k==674105772%12037603 then m(a,H(h,d,u))elseif k==2436771010%13030861 then m(a,H(h,d))elseif k==144419490%1362448 then m(a,H(h))end end S=S+k end k[h]=K(a)end end end end return(function(j,h,u,o,a,k,d,P,f,g,W,N,t,K,S,H,b,B,y,Q,R)g,y,K,t,H,W,S,B,R,N,Q,f,P,b=function(h)local m,Q=-794537-(-794538),h[2396715637%12228141]while Q do H[Q],m=H[Q]-(-739480+739481),(583988+-583987)+m if H[Q]==-840138-(-840138)then H[Q],K[Q]=nil,nil end Q=h[m]end end,function(h,m)local k=P(m)local d=function(...)return Q(h,{...},m,k)end return d end,{},function(h)H[h]=H[h]-(434146+-434145)if H[h]==517132-517132 then H[h],K[h]=nil,nil end end,{},function(h,m)local k=P(m)local d=function()return Q(h,{},m,k)end return d end,473103+-473103,function(h,m)local k=P(m)local d=function(d,u)return Q(h,{d,u},m,k)end return d end,function(h,m)local k=P(m)local d=function(d,u,o,j,a,K,H)return Q(h,{d;u,o,j,a;K,H},m,k)end return d end,function()S=(485627+-485626)+S H[S]=-427955-(-427956)return S end,function(Q,d,u,o)local Si={}local oi,EY,Ki,a,SY,BY,H,n,yY,KY,tY,WY,eY,uY,V,qY,di,CY,C,UY,gY,z,M,nY,GY,AY,q,PY,aY,U,ZY,ai,bY,vY,x,J,s,F,XY,RY,iY,IY,y,D,xY,FY,X,kY,rY,JY,O,mY,I,Ni,T,oY,w,LY,hY,VY,HY,sY,MY,wY,Hi,Z,ui,YY,cY,e,g,QY,Y,A,DY,E,L,zY,hi,lY,TY,l,v,ji,OY,jY,mi,p,G,i,ki,pY,dY,c,fY,Qi,NY,P,S,r while Q do if Q<8622414-472518 then if Q<-498441+4841746 then if Q<304628+1711741 then if Q>438188+919961 then if Q<2458919-576512 then if Q<182621+1317196 then Q=12352783-841517 elseif 2931319868%12257886>Q then U=m(-443-61072)p=h[U]U=m(-1036540-(-975028))i=p[U]Q,L=-65897+7235266,i else a,Q=x,A Q=6410458-417753 end else if Q<2547774979%11624721 then Q=K[u[-293100+293107]]Q=Q and 13370590-269793 or 6710437-(-968757)else Q=K[u[-449493+449503]]S=K[u[-750457-(-750468)]]H[Q]=S Q=K[u[397150+-397138]]S={Q(H)}a,Q={k(S)},h[m(298815-360316)]end end else if Q<1100223-220002 then if Q<-50475+579619 then Q=-369252+4738792<=10161941-(-737528)Q=Q and 382933+2212901 or 8649214-(-668814)elseif-134888-(-973815)>Q then Q={}K[u[1128751507%4607149]]=Q a=K[u[-201414+201417]]g,r,s,y=a,-1008117-(-1008118),121370+-121369,35184371732657-(-356175)a=S%y C,Q=1046208-1045953,3463761718%28966938 K[u[78047+-78043]]=a v=S%C C,i=520783-520781,s y=v+C K[u[2325375265%15711995]]=y C,s=m(733646+-795286),699789+-699789 v=#H P[S]=C C=-305764-(-305968)Z=m(-1096483-(-1034843))L,p=v,i<s s=r-i else P=K[u[-328721+328727]]S=P==H a,Q=S,3265417586%15043877 end else if Q<182439+758305 then H=nil K[u[-815055+815060]]=a Q=1772104-(-151702)elseif-936157+2051704>Q then l=m(-888287+826725)w=h[l]l,r=m(-338621-(-276991)),s n=w[l]w=n(H,r)n=K[u[-658891-(-658897)]]l=n()Q=3973583340%32433502 q=w+l z=q+C r,w,q=nil,1026656141%16558970,582533936%7281671 U=z%q C=U n=C+w q=g[n]z=Z..q Z=z else C,r,g=nil,Z,nil Z=nil P[S]=r v,Q=nil,-973727+9535963 end end end else if 3361709-179804>Q then if Q<95148113%10244319 then if Q<1472540-(-842569)then Q,a=622867295%7807849>-804617+6253975,{}K[u[-454050+454051]]=Q Q=h[m(-459581-(-398025))]elseif 2012763-(-685670)>Q then a,H=m(396005+-457617),m(-635312-(-573886))Q=h[a]a=h[H]H=m(-1062148-(-1000722))h[H]=Q H=m(-672078-(-610466))h[H]=a H=K[u[798251743%6187998]]S=H()Q=1156817-912217 else P=250269-250068 S=K[u[-668134-(-668137)]]H=S*P S,P=616252+-615995,175798-175797 a=H%S K[u[166784799%13898733]]=a S=K[u[-72253-(-72256)]]H=S~=P Q=H and 321326+13024789 or 2151042-(-649991)end else if Q<2985271-(-142199)then Q,H,a=m(-690155-(-628660)),d,461458-461458 S=N()K[S]=Q P=788140-788139 g,Q=P,4778769117%24836198 P=26476330%8825443 y=P P=236791+-236791 v=P>y P=a-y else Z=K[S]r=1308758026%20849593>=7067163250%28900599 a=Z==r Q=a and 637882704%17890119 or 13812466-980052 end end else if Q<3657205-(-172084)then if Q<3682595-398758 then Q=2429854032%15000037 elseif 2048670859%11425132>Q then K[S]=z Q=n n=K[S]Q=n and 7499677-218222 or 1812424433%9715745 else A=K[S]I,x=A,Q Q=A and 2683268888%27264805 or 12467334-(-656849)end else if Q<-810818+4906651 then n=B(9341664-401992,{g})w={n()}a,Q={k(w)},h[m(-308530-(-246893))]else a=K[S]Z=m(507199+-568694)Q=a~=Z Q=Q and 155059214%17065422 or 962333+7970544 end end end end else if Q>5746691-(-87048)then if Q>6668043-(-557369)then if 485489063%20769656>Q then if Q<768987+6584205 then Q=1858860542%16837543 elseif Q<-698406+8250467 then Q=K[u[112441617%1003943]]S,Z,r=P,569547-569547,482206-481951 C=Q(Z,r)H[S]=C S,Q=nil,-224498+11835614 else P=K[u[-63473-(-63482)]]S,Q,g=-836175-(-836176),{},P H,P=Q,-299584+299585 y,Q=P,12519648-908532 P=-852431+852431 v=y<P P=S-y end else if 1952567976%18519805>Q then P=-60329-(-60542)S=K[u[1913881202%8285200]]H=S*P S=27552854403465-(-67732)a=H+S H=35184372233539-144707 Q=a%H K[u[342478+-342476]]=Q Q=1003439825%13897761 else M=t(M)O=t(O)F=nil X=t(X)V=t(V)Q=1855916999%17244880 J=t(J)D=t(D)end end else if Q<6686512-11622 then if Q<6950981-718738 then Q=I Q=2325590443%18392923 K[S]=a elseif 7563145-1017770>Q then Q=14375183-(-472892)else O,Q=m(600786+-662398),2553902651%19620741 n=h[O]O=m(110946-172372)h[O]=n end else if Q<-184916+7135006 then P=t(P)p,L,U=nil,nil,nil q=t(q)C=t(C)S=t(S)v,P=nil,nil y=t(y)g=t(g)y=N()Z,g,Q=nil,1033670-1033668,3122258916%27978023 S,C=nil,m(853612-915211)s=t(s)i,s=nil,m(-376319-(-314804))K[y]=g v=h[C]C,L=m(-383690+322045),m(-376554+314992)r=t(r)p=531515+-531259 g=v[C]v=N()C=N()K[v]=g g,U=-986464+986464,p K[C]=g Z=N()g={}K[Z]=g r=h[L]p,L=274848+-274847,m(-511377+449794)g=r[L]i=m(441272-502871)L=h[s]s=m(485508+-547055)r=L[s]s=h[i]i=m(165704-227171)L=s[i]i=111387-111386 s={}q=p p=547853117%6155653 O=q<p p=i-q else a,Q=L,s Q=L and 9100224-(-690461)or-25056+15703275 end end end else if 134981+4956129>Q then if 714301035%9337579>Q then if Q<907370+3482233 then Q=673332+10837934 elseif 1338129217%20207545>Q then H=K[u[-203095-(-203096)]]a=#H H=424750-424750 Q=a==H Q=Q and 894931+6999826 or 9785605-(-354188)else P,S,a=340718+3541999,m(-438957+377352),11861014-960739 H=S^P Q=a-H H,a=Q,m(-365698-(-304226))Q=a/H a={Q}Q=h[m(-679416+617962)]end else if-644319+5502146>Q then Q=5636926-77195 C=K[y]a=C elseif 2736539173%11774293>Q then c=1005586228%6572459 Y=F[c]c,A=4636854-928932<87981279%3680828,Q e=Y==c x,Q=e,e and-570458+10845530 or 1865209496%9654759 else Q=a and 15102796-581531 or 1554307138%15370132 end end else if 320893709%16599547>Q then if 5366952-91461>Q then Q,a=h[m(851424-912924)],{}elseif Q<-189730+5560112 then Q=3603111095%14170219 else Q=13908508-899094 end else if 532754+5084498>Q then r,Z,Q=m(-686092-(-624577)),m(896141+-957740),v v,p,s=a,m(-958639-(-897124)),Q C=h[Z]Z=m(-1020505-(-959038))a=C[Z]C=N()K[C]=a Z=h[r]r=m(851749-913278)a=Z[r]Z,r=a,Q i=h[p]Q,L=i and 1218588-(-310631)or 7973965-804596,i else w=K[S]z,n=w,Q Q=w and 11800503-(-270063)or 2646006-(-715348)end end end end end else if Q>552255+11625782 then if 13312490-(-191842)>Q then if 12220402-(-834703)>Q then if Q<78714+12912385 then if 3769368889%24715940>Q then Q,g=3098229646%16160859>-636888+7076520,m(-960620+899058)v=Q K[S]=Q P=h[g]Z,g=m(780019+-841536),m(-713183-(-651685))a=P[g]g=N()P=N()y=N()K[P]=a a=B(341595+12648559,{})K[g]=a a=2774699068%14432162>7476884-(-886986)K[y]=a C=h[Z]r=B(-769886+2804270,{y})Z=C(r)Q,a=Z and 521890+4314470 or 634997+4924734,Z elseif 13955146-1043862>Q then Q=-557499+12045808 else a=m(-352346+290916)Q=h[a]H=m(660165-721771)a=Q(H)Q,a=h[m(-462671+401214)],{}end else if Q<13251896-251167 then S=K[u[2807572102%16515130]]P=K[u[-475984+475987]]H=S==P Q,a=237680348%5968032,H else U=#s p=-278764-(-278765)i=L(p,U)p=r(s,i)i,M=nil,-16353+16354 U=K[Z]O=p-M q=g(O)U[p]=q p=nil q=#s O=56363249%405491 U=q==O Q=U and 12701570-(-634810)or 12022543-(-986871)end end else if-158312+13397147>Q then if Q<2609245474%20441992 then P,H=1539719759%8506739,m(167122+-228552)Q=h[H]S=K[u[2017807208%13452048]]H=Q(S,P)Q=558169261%13426587 elseif 678132+12454605>Q then K[S]=I G,Q=714669-714668,x c=K[V]Y=c+G e=F[Y]A=L+e e=90031+-89775 x=A%e Y=K[J]e=i+Y L,Y=x,878152775%4457627 A=e%Y i,Q=A,7292837-(-789308)else y,g=2090569912%14619370,3198936385%16661127 S=K[u[1118386%24853]]P=S(g,y)S=-78180-(-78181)H=P==S a,Q=H,H and 384685+4542415 or 724012901%29625869 end else if 669527+12671720>Q then Si[882694-882552],di,Si[-965819+965888],Si[-608729-(-608837)]=m(-700397+638809),-150611+31322275284300,860922+23126829041431,m(-995354-(-933741))q=N()Si[351463+-351367],ZY=m(-16511-45084),10292018571369-(-813647)p=N()Si[445383-445281],i,Si[-848652-(-848795)]=m(507162-568614),{},12971196201204-975196 K[p]=i O,J=m(-511965-(-450358)),m(701412+-763004)U=W(3521645-(-887148),{p,C,y,v})i=N()r,Si[-631237-(-631323)],Si[209980+-209940]=nil,m(-721863-(-660360)),m(-912625+851157)K[i]=U F,Si[787029+-786863],wY,L,Si[-109243+109270],Si[-1019816-(-1019938)],Si[181277086%10070942],M,ki,U,Si[1540710533%11851619]=nil,m(204736-266332),31367904043644-76142,nil,1382055085358-869035,m(-187952-(-126323)),m(792082-853576),{},m(-890188-(-828655)),{},467588+24160049088878 K[q]=U Si[392795+-392782],Si[-557134+557229],g,Si[431079+-430896]=-185097+9382467134490,30999619781573-576354,nil,34037541848147-(-506262)U=h[O]eY,gY=988198+2454294605904,-220055+10415686807177 V=K[q]X,aY=m(-104717+43083),-844346+18047205065485 D,Si[859675-859518]={[J]=V;[X]=F},4414755269861-(-465698)v=t(v)Si[73392299%1164957],yY,GY,Si[124413022%2145052],bY=m(276722+-338243),22431875695246-(-517695),m(96910+-158448),m(-1102752-(-1041309)),18446716502959-926242 O=U(M,D)Ni,P,Si[-540763+540805],Si[738646718%5314004],Si[291881899%12690514],hY=m(408654-470079),O,m(596827+-658379),m(1013127+-1074576),14018743701701-(-231610),630303+4566594742831 U=R(-843422+9061070,{q,p;Z;C;y;i})VY,Si[-468646+468700]=851853+28419279205412,m(1012313+-1073935)q=t(q)Si[299819+-299767],sY,r,Si[225997469%6646980],kY,QY,Qi,Si[248475+-248349],s=m(-582320+520730),-727038+27139736979803,12834712628693-5757,-1042785+20564861931209,m(-442050-(-380558)),3828369453039-76025,23335222269067-(-710119),m(501159-562756),nil p=t(p)Z=t(Z)C=t(C)i=t(i)Z,C,S,jY,fY,qY,Si[40070155%8014021],XY,HY=22126428736410-123739,m(-403559-(-341949)),U,m(439543+-501067),17366406475451-(-995547),144084+14081792616137,m(-311875+250321),m(47465-108979),-999876+29523638089592 y=t(y)y=m(354878+-416400)g=h[y]y=g()Si[-157417+157597],Si[1338556447%8525837],vY,Si[359739-359578],q,tY,hi,Si[859377420%10742216],Si[412761149%2267918],Si[1028779-1028772]=m(212123-273704),m(-619497-(-557936)),34226478561934-162893,-611964+5773824106748,m(133071+-194647),m(224418+-285841),466066+6762923012027,m(-829877+768299),-555186+15465640318163,34151152609453-158351 v=S(C,Z)Si[566850-566711],Z=13482240597881-(-227597),m(-677700+616193)g=P[v]C=S(Z,r)Si[2948743241%12547843],CY,WY,Z,NY,KY=m(-1038986+977347),m(-811171+749577),m(881655+-943244),18063687728284-(-926783),m(-457681-(-396066)),m(-1025243+963774)v=P[C]D,C,X,xY,oY=m(-988028-(-926412)),m(926897+-988378),770635+4828406089341,522278+3027820449115,7679232857348-689933 y[g]=v r,Si[119944143%1223919],Si[164196324%4829303],y=m(-536556-(-474936)),-514520+24073799697826,m(-551774-(-490209)),m(-259768-(-198246))g=h[y]F=m(583347-644783)y=g()mY,s=m(-975222-(-913581)),m(-1011031+949465)v=S(C,Z)Si[462679-462554]=221466+3630013261184 g=P[v]Z,LY,PY,L,Si[1052057451%6081256],Si[440616-440599],Si[-764632+764786],i,Si[868228-868144],Si[667397043%6296198],p,Si[581235+-581220],oi,v,Si[-458360+458430],Si[-514177+514221],Si[546733+-546669],J,Si[800867252%9312408]=-355116+33503605319709,m(196634+-258111),m(-1046241-(-984654)),25237641129183-(-934153),613782+26214868374041,13201420957371-(-909640),m(-705988+644483),-895449+4982197891817,m(970664+-1032177),436529+11622704049139,m(297979+-359468),949040+18991127717723,12275578557432-(-295516),9177913104-(-1037526),m(856441-917999),m(-867317+805754),m(-596461-(-534906)),-907589+8545819420880,m(260060+-321542)y[g]=v UY,SY,y,Si[-80418+80428]=-368040+27088935259886,21555347012770-(-813715),m(93631+-155153),m(-170255-(-108744))g=h[y]Si[116503439%3426569],Si[-541784-(-541804)],lY=-71790+5195324973537,m(-903359+841869),m(895835-957435)y=g()DY,Si[-584587-(-584672)],C=m(-193297-(-131788)),16976131672376-879191,m(-258434+196848)v=S(C,Z)Si[-534153-(-534297)],Si[1248567049%10671513]=m(192795+-254334),m(-914127-(-852504))g=P[v]FY,nY,Z,E,v,Si[645440824%5042506]=321921+32335369097552,m(-207507+145973),32235748569236-390642,-407185+14106977161274,927894+-927893,m(154999+-216490)y[g]=v Si[501215269%13189872],Si[2880970748%16749829],y,C,BY=-663980+34647869661362,m(-521066-(-459601)),m(-609390+547868),m(-875853-(-814407)),m(-1027474+965873)g=h[y]y=g()v=S(C,Z)C,Si[1441132205%5629422]=m(193029-254586),804053+6199860495986 g=P[v]U,v=-369561+21355819158129,-959040-(-959042)y[g]=v ai,Si[2073276243%16454573],Si[651262-651259],y=2257828651823-1023764,24201970218232-(-882445),2219987591663-138726,m(-684706+623184)g=h[y]G=m(-843550+782065)y=g()Z,T=22367117954099-(-23676),m(-61522+-14)v=S(C,Z)Si[384347+-384311],M,Si[830545+-830524],Si[-579052+579117]=m(-723130+661664),573526158136-780845,18033234192556-(-768033),-982560+33652735884118 g=P[v]V=m(-865689-(-804139))Z=S(r,L)C=P[Z]L=S(s,i)e,Si[414525315%14293973],Si[1041176-1041070],Z,c,Y,Si[686930-686796],Si[102691416%11410140],Si[1023102+-1023078]=28294455091853-945942,m(-425732+364148),m(892974-954577),-926110+10334513>=8702042-(-600055),-446038+5512655820893,m(-805205+743656),m(48562+-110209),m(606192-667710),m(-820128-(-758555))r=P[L]i=S(p,U)Si[1156313424%10417237],L,Si[859256-859142]=-752037+19578124885313,2722167984%13801843<=-619117+8637970,m(-775415-(-713783))s=P[i]Si[994983+-994974]=31743625372931-813894 U=S(q,M)i=10879333-(-90952)<15065845-(-310854)p=P[U]zY,dY,U=m(-874393-(-812750)),35146532037781-107687,963885+9212204<1446036561%27529173 M=S(D,J)EY=440211+18506815678998 q=P[M]M=5516987-(-750241)>-953054+4291766 J=S(V,X)uY=m(950983+-1012553)D=P[J]Si[-593087+593257],Si[-462976-(-463029)]=m(94925-156387),-1017530+29174920821707 X=S(F,e)V=P[X]Si[-1036275-(-1036294)]=868976+26748873551415 e=S(Y,c)F=P[e]J,Si[434485+-434378]=9478946-(-464774)<=2645877047%14240683,10817712908497-677156 c=S(G,E)Si[10634+-10457],Si[-623357-(-623473)],X,e,Si[51499116%10299810],Si[794714+-794688],Si[-135696+135700]=28070024036744-527993,m(-1016238-(-954758)),2915019346%11979213>=-439344-(-756614),44966-(-107261)<15004682-(-492303),m(99516-160995),m(-341133-(-279569)),m(-15339+-46139)Y=P[c]E=S(T,hY)Si[-521990-(-522101)],Si[-648555+648684],c=7955419804932-173708,-641165+17431889029186,2505990444%13260960<=14137031-(-747665)G=P[E]iY,Si[1017154-1017031],E,RY=392631+18533190951935,-608422+31905327628975,3042751-139207~=6569972-(-945911),m(-831638-(-770095))hY=S(mY,QY)T=P[hY]QY=S(kY,dY)mY=P[QY]hY,Si[524278195%4681055],Si[159029-159024],mi=4678955862%19853677>=642231+10078565,25366255823285-326545,8383729606617-(-962406),m(505077-566553)dY=S(uY,oY)AY,Si[641831484%3413997],Si[909992223%9009823]=m(-613325-(-551785)),m(-697690-(-636193)),m(100228-161681)kY=P[dY]Si[452366+-452286],Si[621515-621425],QY,Si[1741536193%15276633],OY,Ki=m(-327639+266037),m(-34933+-26711),1105365238%8822073~=5613736-699872,338094+32786031006453,9968252218374-776677,m(534860-596383)oY=S(jY,aY)Si[-682266+682385],dY=14654335303399-(-728000),3237524984%12977446~=1470770032%23106033 uY=P[oY]oY=1371346-(-680941)~=13966631-(-557053)aY=S(KY,HY)jY=P[aY]JY=m(-503175+441648)HY=S(NY,SY)cY,aY,Si[358597+-358445]=m(219315+-280755),-501625+12558846<=15139772-(-371428),m(939699+-1001162)KY=P[HY]Si[658844-658814],rY,HY=m(142002-203530),m(-1019967+958481),-638609+5374545>2837402-32832 SY=S(PY,gY)NY=P[SY]Si[-975778+975913],SY,Si[2401306999%10625252],Si[385713+-385641]=-415789+32897528583172,-572007+3270194>1013305+999782,-902821+5839697727812,m(-682649-(-621174))gY=S(tY,yY)Si[433267654%1996625]=-957623+15398004996281 PY=P[gY]gY,pY=-376156+10681171>1083729555%12735833,m(-711394+649841)yY=S(BY,bY)Si[464687+-464625],Si[416014+-415899],MY=m(96724+-158370),214266+9719143271603,-462056+12401026098038 tY=P[yY]Si[978335+-978296],yY,TY,Si[1790030000%8564736],Si[248590+-248496]=25984866483861-347985,486883298%5486233<16104995-797621,m(404253-465697),m(275192-336777),m(318522-379995)bY=S(WY,fY)BY=P[bY]fY=S(RY,vY)bY,Si[993056-992919]=400265224%5592474>=593477526%3407443,200962+24081767946955 WY=P[fY]fY,IY,Si[-573098-(-573123)],Si[-715337+715351],Si[209282895%1283944],Si[-180662+180738]=3166554298%22520709>=-980964+13620628,m(-742458-(-680975)),18704238851976-267651,m(-456244-(-394736)),23493440547129-(-704898),m(796012+-857584)vY=S(CY,ZY)RY=P[vY]Q,vY,Si[217098-217023],Si[1959379324%9155978]=h[m(1038267+-1099878)],-298070+5794557<=13995949-(-924759),1019481+32509295832265,m(741422+-802880)ZY=S(rY,sY)CY=P[ZY]sY=S(pY,iY)ZY=1102336296%8009765<=3557485123%25867928 rY=P[sY]iY=S(LY,UY)sY,Si[-96888+96921]=804091845%20899333>503871651%7289494,49308+32749958134518 pY=P[iY]iY,Si[1563467567%9710978],Si[-264547+264565],Si[-952106+952210]=4775458675%21760616>1357741-383785,-147032+15728595933940,m(-688871-(-627400)),m(964286+-1025877)UY=S(zY,qY)LY=P[UY]qY=S(lY,wY)Si[2534395150%9977933]=m(-900240-(-838666))zY=P[qY]UY,qY,Si[180066-179983],Si[222623+-222562]=4898383739%31911901~=213821+726076,8339246-469892~=-827059+5138285,32051979115722-221821,12327202750198-(-137078)wY=S(nY,OY)Si[472459900%5832836],Si[2417104438%12025395]=m(950545-1012004),-873709+12456981359509 lY=P[wY]wY=-522261+4954330<10269227-(-360563)OY=S(DY,MY)nY=P[OY]YY=989415+33401476064218 MY=S(JY,VY)Si[1027543+-1027541]=m(78425+-140067)DY=P[MY]MY=73846+4256550<=23963452%12494983 VY=S(XY,FY)JY=P[VY]Si[387949727%5542138],VY,Si[109875829%4777206]=20710932905602-(-567082),924499650%13320379<=10650563-(-555949),1034379+32374133813848 FY=S(IY,eY)OY,Si[-15807-(-15858)],Hi=2712674-(-738638)<8090560-(-677694),-952520+30964895531291,40861305184557%704505382157 XY=P[FY]eY=S(AY,YY)ji=m(-1054271-(-992654))IY=P[eY]Si[434462+-434451]=18359+29939078377150 YY=S(GY,EY)Si[-225833+225834],Si[-971706+971722],eY,FY,Si[689627+-689509]=698898+16103947531064,m(287861-349499),1494156881%7656042<464812+8165089,1031845+13195236>=1381558213%14652770,m(389186-450705)AY=P[YY]EY=S(cY,xY)GY=P[EY]YY,Si[1478351668%14783516]=2740249563%14444401~=9064914-155662,m(930150-991764)xY=S(TY,hi)Si[617621+-617447],EY=m(187773+-249298),16379765-291138~=3173056115%28220496 cY=P[xY]Si[1112428569%5348214],Si[441565-441553],xY,ui=8056102114733-788230,m(828155+-889592),11412928-(-469745)<2052826450%28719249,m(-599119-(-537669))hi=S(mi,Qi)TY=P[hi]hi,Si[238857976%11374184]=3291844976%20271618>=793704534%17225904,m(892338+-953898)Qi=S(ki,di)mi=P[Qi]Si[595847-595727]=m(-640000-(-578382))di=S(ui,oi)ki=P[di]Si[-493386-(-493464)]=m(403018+-464474)oi=S(ji,ai)ui=P[oi]Si[283790406%6038092],oi,di,Si[-466732-(-466821)],Si[-664878-(-664966)]=m(485653+-547233),2262116124%19907859>560422+4090452,647495839%10378721<2756615590%19593074,33434033290290-180066,m(714597-776038)ai=S(Ki,Hi)ji=P[ai]ai=-657247+16389476>3936923943%24680244 Hi=S(Ni,Si[4958-4957])Qi=1605760776%20936935~=1239920516%14058340 Ki=P[Hi]Hi,Si[995931-995828]=-98599+16558870>13445425-(-735903),947323+9888897998209 Si[2601093883%10883238]=S(Si[568799156%13542837],Si[-123523+123526])Ni=P[Si[750315313%4631576]]Si[953545726%9631775],Si[-309928-(-310020)],Si[304963318%4484754]=2399122256%13194196>=382671+5052866,m(-42031-19430),m(217458-278928)Si[-294959-(-294962)]=S(Si[-423953+423957],Si[124770-124765])Si[-613215-(-613217)]=P[Si[156678412%9216377]]Si[-621722+621725]=1155811153%7847030<-507964+11578874 Si[39704+-39699]=S(Si[1900388784%16670077],Si[1904522631%14879083])Si[152169090%2056339]=P[Si[638278-638273]]Si[-700271-(-700278)]=S(Si[-428702-(-428710)],Si[-824058+824067])Si[33958452%1061197]=m(-181297+119756)Si[1837839750%8835768]=P[Si[768688072%5301297]]Si[727396+-727391]=2995764332%28941640>708542+9063342 Si[663223950%13004391]=S(Si[2210103972%9132661],Si[-33646-(-33657)])Si[-958234-(-958241)]=4049894-500414<6554683-(-1039521)Si[142832+-142824]=P[Si[219645806%12920341]]Si[315011371%9545798],Si[-154562+154571]=10002684782838-(-92475),11175933-274323>528372354%4964667 Si[115392908%12821433]=S(Si[898534332%8809160],Si[2188979715%8862266])Si[2371753225%12162837]=P[Si[352224+-352213]]Si[275779993%7660555]=S(Si[2303649330%13315892],Si[-888559-(-888574)])Si[2025524238%10178513],Si[839992955%11351256]=-983306+8599509618862,2531198551%15364095<=344543+14926524 Si[-254602+254614]=P[Si[-355698-(-355711)]]Si[2999111370%11761221]=S(Si[-752777+752793],Si[996398-996381])Si[1522128494%6342202]=P[Si[1797643395%9218684]]Si[759257-759244],Si[90600903%3235746]=491142-(-560353)~=1058014-266421,-630516+14428533>=722993+8968840 Si[2228010433%11664976]=S(Si[775253-775235],Si[-555234+555253])Si[-273350-(-273366)]=P[Si[1019692-1019675]]Si[639281-639264]=2796617-(-923324)~=12850640-(-390673)Si[1025945+-1025926]=S(Si[-226155-(-226175)],Si[697917-697896])Si[890027283%3490303]=P[Si[-439635+439654]]Si[977404617%10623963]=S(Si[192347-192325],Si[-968592-(-968615)])Si[789477331%3795564]=1819017794%7880520~=2284498805%16829345 Si[45742010%788655]=P[Si[435990981%9083145]]Si[1761635312%14093081],Si[727455-727302],Si[265556865%14753158]=-338226+26730793703889,5361738668608-(-470912),14967992-719578~=13384891-(-564723)Si[832517-832494]=S(Si[-168286-(-168310)],Si[-995896-(-995921)])Si[2257376962%10749414]=P[Si[34666819%753626]]Si[248952005%2464871]=m(-949316-(-887692))Si[827544939%8193514]=S(Si[-796090-(-796116)],Si[328961763%9137826])Si[-1036998+1037021]=9191985-763090<=943336+8767527 Si[389546+-389522]=P[Si[443686-443661]]Si[641820-641793]=S(Si[-68309-(-68337)],Si[716700+-716671])Si[394319+-394294]=390739-(-103790)<=3940940657%16645161 Si[-121864+121890]=P[Si[-831553-(-831580)]]Si[138987717%5147688],Si[148309317%716470]=26380217912323-203783,246516915%12812078<=808998835%15053082 Si[-24086+24115]=S(Si[-735977+736007],Si[958904366%14312005])Si[-74710+74738]=P[Si[-124964-(-124993)]]Si[965523371%5679549]=22517253670936-859939 Si[999526856%4782425]=S(Si[377389+-377357],Si[178427+-178394])Si[2675883720%11533981]=m(468606-530126)Si[-714003+714033]=P[Si[-178682+178713]]Si[-757495-(-757622)],Si[688012+-687981],Si[796547+-796518]=-699388+4435882341389,-178261+8227586>1214896301%6916349,1535080-(-236197)<258595+14646835 Si[-328918-(-328951)]=S(Si[555926-555892],Si[987946+-987911])Si[755259248%15734567]=P[Si[35187284%3198841]]Si[-281654+281689]=S(Si[78743+-78707],Si[-162206-(-162243)])Si[970715-970681]=P[Si[869018-868983]]Si[904146+-904109]=S(Si[781750+-781712],Si[500616+-500577])Si[860772003%15370928],Si[-69014-(-69073)]=1096114578%11811983<-269381+11082630,712585+31432746736036 Si[796779432%8130402]=P[Si[222836+-222799]]Si[88700236%8870009]=m(543166+-604774)Si[570378-570339]=S(Si[364333-364293],Si[221572-221531])Si[-670827-(-670865)]=P[Si[922169-922130]]Si[687362-687325]=3858275-(-48269)~=-586124+11893902 Si[-709455+709496]=S(Si[3212880206%13007612],Si[-809288-(-809331)])Si[110258272%15751177],Si[1544154661%6684652],Si[-660184-(-660242)],Si[650702+-650663]=291354+3431805~=9160708-656091,765920+15484800691274,m(-860499-(-799070)),954661+-477306<=71473913%12313705 Si[163591960%13632660]=P[Si[-518474+518515]]Si[88176464%2099437],Si[-145742-(-145783)]=m(-966757-(-905122)),35863+12777968<=12324440-(-668380)Si[34018-33975]=S(Si[955740-955696],Si[158923341%4182192])Si[-324191-(-324322)]=962964+26756842438423 Si[315445746%15021224]=P[Si[562641+-562598]]Si[362527864%5943079]=S(Si[933960595%8414059],Si[257414+-257367])Si[-679940-(-679983)]=-764150+2051858<13870413-(-893684)Si[1019843924%4635654]=P[Si[1495885601%7999388]]Si[719176-719009],Si[875122293%4808364],Si[599238465%10512954]=698587+33428813075443,1418334-(-329419)<=131426032%29476784,150876+7593665511540 Si[-383616+383663]=S(Si[616978-616930],Si[1678906729%13990889])Si[-1022705+1022751]=P[Si[287066+-287019]]Si[358713-358608],Si[992986+-992939]=-981490+27654991260735,35972541%10468654<3463412395%18175537 Si[99924159%7686470]=S(Si[-357844+357894],Si[-574865-(-574916)])Si[-176984-(-177032)]=P[Si[1191051182%11131319]]Si[67205+-67131],Si[614228+-614046]=m(-526267-(-464807)),m(-489802+428254)Si[409636339%5611456]=S(Si[-168673-(-168725)],Si[-413913+413966])Si[1467954303%13224813]=m(-1073276-(-1011849))Si[506095+-506045]=P[Si[347766-347715]]Si[-182583-(-182636)]=S(Si[449968092%6337578],Si[281674-281619])Si[73573465%791112]=15642610-517134>-89255+7340353 Si[377192+-377140]=P[Si[1117941955%14518726]]Si[406918-406839],Si[440451-440266],Si[-388015+388086]=28667061359050-(-287323),547402+22498939817634,30211986630429-(-724951)Si[-838251-(-838306)]=S(Si[-639666+639722],Si[1374092305%10819624])Si[947938290%5815572]=P[Si[26911-26856]]Si[-906948+906999],Si[602272-602151],Si[989407+-989352],Si[1039907-1039854]=-797681+12119778~=8499490-771037,4.1772692152111e+14%5967527575244,1366685541%28810893>8807013-751340,-309635+5215826>=4139539-374471 Si[6193+-6136]=S(Si[-139043+139101],Si[17844063%4461001])Si[-184318-(-184374)]=P[Si[-599791-(-599848)]]Si[529672+-529613]=S(Si[913487+-913427],Si[1222047061%12220470])Si[-79761+79818],Si[-176584-(-176681)],Si[174827431%5141979]=-84169+5002771>859990596%8568939,22556017462689-(-777062),-585054+10349848215601 Si[440407088%6291529]=P[Si[240006739%7059020]]Si[2901122681%13620294]=3282964174%29707743>456682+4387767 Si[-829991-(-830052)]=S(Si[395978722%11313676],Si[322603647%1414928])Si[707334261%8420644]=-51092+2622284287065 Si[1704889716%13424328]=P[Si[1229083695%10415963]]Si[-937993+938054]=11228058-314634~=705584+10829207 Si[-488083-(-488146)]=S(Si[478123+-478059],Si[-453908+453973])Si[850257+-850195]=P[Si[531156-531093]]Si[-907604-(-907667)]=32975+1862252<=14026492-(-423138)Si[1394013109%7414963]=S(Si[866290+-866224],Si[1028318722%9793511])Si[1035780+-1035716]=P[Si[-498113-(-498178)]]Si[-461152-(-461217)]=7066381-(-749030)<=1797477604%30230117 Si[-883847-(-883914)]=S(Si[-321382-(-321450)],Si[191779014%12785263])Si[223800804%4567362]=P[Si[1302352547%8139703]]Si[-916879+916948]=S(Si[30650+-30580],Si[843333903%9583339])Si[1255798561%5146715]=-657979+21800113893858 Si[-6068-(-6136)]=P[Si[1367997894%6422525]]Si[-802868+802937],Si[301849-301711],Si[796100+-796033]=808871289%20916111>1563389212%9754960,m(-754585-(-693016)),594689+11349112~=2346828958%23400297 Si[353518745%3101041]=S(Si[578619424%3196792],Si[2307192121%9155524])Si[2854625580%11373010]=P[Si[-956931+957002]]Si[880757544%4709933]=S(Si[144799949%13163625],Si[-645360+645435])Si[643488118%3574933],Si[-521451-(-521522)]=m(-355251+293800),-161228+5594558<=5344056-(-480932)Si[188794071%2030043]=P[Si[1018809-1018736]]Si[112127035%1401587]=S(Si[-493477-(-493553)],Si[1706161754%8163453])Si[425516+-425442]=P[Si[332865+-332790]]Si[20289365%845387]=S(Si[2855310354%12861758],Si[-422621-(-422700)])Si[199897+-199824]=7127595-(-591057)<=9039302-(-39514)Si[-620785+620861]=P[Si[609+-532]]Si[580115+-580040]=459151534%4941780>935500+2279524 Si[522500-522421]=S(Si[1034174-1034094],Si[58037241%9672860])Si[108853662%922488]=P[Si[-665805-(-665884)]]Si[293982+-293858]=m(-847314-(-785747))Si[-327112-(-327193)]=S(Si[91532-91450],Si[2023985081%16063373])Si[481447078%4863101],Si[-245640+245717],a=1254506799%15591910>=991886272%14941257,4243524-566715<=-297803+6158489,{}Si[52339+-52259]=P[Si[106988-106907]]Si[920636325%13949034]=705879+15847256~=9204943-459638 Si[1760547963%10356164]=S(Si[2591666154%12341267],Si[520805-520720])Si[-314398+314480]=P[Si[-486672+486755]]Si[58474255%769397]=4002828-980641<-159578+6186738 Si[-530025-(-530110)]=S(Si[-973125-(-973211)],Si[-1014631-(-1014718)])Si[1048245-1048113]=m(1753+-63380)Si[945829+-945745]=P[Si[543844+-543759]]Si[-862257+862342]=4025769193%28449965>=534058+10926431 Si[316330+-316243]=S(Si[205612-205524],Si[1942891733%15668481])Si[1886220002%9623571]=P[Si[1208775747%8823180]]Si[-541985-(-542074)]=S(Si[1024992639%12654229],Si[641525+-641434])Si[-124296+124383]=859880+972753~=14623307-42401 Si[299750-299662]=P[Si[451180-451091]]Si[369622086%5063315]=S(Si[919000-918908],Si[1074117661%5565376])Si[5937796%5937706]=P[Si[653987962%9761013]]Si[217850-217692]=m(-277730+216226)Si[130739589%1790952]=S(Si[1586764256%6247103],Si[372136-372041])Si[-270168+270257],Si[220020791%2200207]=344199+13121257>344477673%10942686,7549804-(-95413)<8201361-(-729854)Si[-270667+270759]=P[Si[416699677%2147936]]Si[555909+-555814]=S(Si[1727676328%11366291],Si[-828252-(-828349)])Si[-676874-(-676973)],Si[1553446363%10022234]=-478385+15198010271830,190045+14901413~=287364+378977 Si[1015717-1015623]=P[Si[2305616612%15069389]]Si[285359-285264]=3757981783%32537677>-803766+8775693 Si[186172+-186075]=S(Si[1280920178%5822364],Si[1073236394%5235299])Si[-574552-(-574648)]=P[Si[984822475%11451423]]Si[822339+-822242]=603927+5406265<16474393-857249 Si[794637+-794538]=S(Si[68624-68524],Si[-1001167-(-1001268)])Si[-942660-(-942758)]=P[Si[223468-223369]]Si[-46254-(-46367)]=-560327+6598235265223 Si[296428+-296327]=S(Si[65182+-65080],Si[-486980+487083])Si[-741639+741739]=P[Si[772221+-772120]]Si[105742+-105641],Si[67348515%488032]=3483584-266185~=17411+15441195,798898386%17329701~=-393254+15507787 Si[3166530625%14263651]=S(Si[-395440+395544],Si[-799428-(-799533)])Si[206246-206144]=P[Si[3215912803%14617785]]Si[-114012+114117]=S(Si[-1042524+1042630],Si[643962+-643855])Si[398209579%4063362],Si[161114+-160928]=734381-(-769781)~=13244110-(-528737),m(-811925+750451)Si[1372117442%6895062]=P[Si[920173-920068]]Si[1610380549%9362677]=897416549%14814672~=53834-(-25464)Si[-770027+770134]=S(Si[579141808%5791417],Si[971815989%5716564])Si[916961+-916782]=-663443+25777986096758 Si[215722+-215616]=P[Si[-538474-(-538581)]]Si[-199082+199189]=765378+5115125<=674985+13955225 Si[-513417+513526]=S(Si[1353621260%9024141],Si[589637+-589526])Si[-1010744+1010852]=P[Si[223820+-223711]]Si[-143794-(-143903)]=9568261-294862<172737+11156165 Si[-305257+305368]=S(Si[684559959%8247709],Si[1640022793%8241320])Si[752171+-752021]=m(-907799-(-846220))Si[-197549+197659]=P[Si[-58729+58840]]Si[113837856%1173585]=407059+10062924~=10044821-(-655793)Si[179697863%1437582]=S(Si[1115492210%4497952],Si[717204+-717089])Si[1044031282%13385015]=P[Si[1010438+-1010325]]Si[419197+-419082]=S(Si[-572666-(-572782)],Si[172617885%7192407])Si[-521546+521660]=P[Si[149460+-149345]]Si[681631+-681472],Si[-642447-(-642562)]=27917757591960-212688,1666566795%16193102>1589628450%17629599 Si[-890724+890841]=S(Si[664322+-664204],Si[163432615%2636008])Si[-501794-(-501907)]=822766+11419595>5935733-(-451555)Si[727149+-727033]=P[Si[324901+-324784]]Si[-420277-(-420394)]=2050921671%14631677<=1464154851%27858261 Si[-265357-(-265476)]=S(Si[959938-959818],Si[314093-313972])Si[267749452%9916642]=P[Si[273128+-273009]]Si[394882897%2309256]=S(Si[1492735646%14634662],Si[705430-705307])Si[-103575+103694]=668496+1225840<-743575+8338305 Si[14442735%14442615]=P[Si[990939+-990818]]Si[265290517%12632876]=3969448128%22248828~=7560523-(-177965)Si[25981699%6495394]=S(Si[-10494+10618],Si[105536-105411])Si[89061882%1391590]=P[Si[-916149+916272]]Si[926839-926714]=S(Si[-869874-(-870000)],Si[658204-658077])Si[18101+-17977]=P[Si[-194521+194646]]Si[-213418-(-213573)],Si[-77473-(-77596)],Si[2280708623%10047174]=-499649+25760186306204,5405379110%30625682~=7306769-819534,1427722454%8381182~=1434429099%18117470 Si[46712727%212330]=S(Si[490304-490176],Si[760162+-760033])Si[205359692%1229698]=P[Si[-956641+956768]]Si[-889646+889773]=134880471%7157662<16377785-986455 Si[319454904%7098995]=S(Si[-396140-(-396270)],Si[1516608275%7153812])Si[-314207+314388]=-154888+23100780021517 Si[1948968442%7764814]=P[Si[425418-425289]]Si[-474645+474792]=8171977213027-816518 Si[754108643%15710594]=S(Si[2822443302%12113490],Si[683438+-683305])Si[2226420698%11021884]=P[Si[-800944+801075]]Si[1170847783%4778970]=S(Si[-652950+653084],Si[-449267+449402])Si[-486189+486318]=-1002809+7162035<=2585648506%21461019 Si[-276771+276903]=P[Si[3036351803%13201529]]Si[2065788853%8866046]=S(Si[184489+-184353],Si[-435314+435451])Si[374677333%5592197]=P[Si[567866+-567731]]Si[-962762+962893],Si[445044181%9271751]=156015+145936<=839990+10066301,2102777044%20779473~=11208141-(-121851)Si[1014496-1014359]=S(Si[394826844%6807357],Si[-737763-(-737902)])Si[-459373+459508]=2946028368%15628921<=2327879583%20127437 Si[-191729-(-191865)]=P[Si[751076+-750939]]Si[-604411-(-604548)]=2040388998%17871364<=5129377-1043660 Si[-852878-(-853017)]=S(Si[112981820%3228048],Si[-955467+955608])Si[-389178+389350]=m(-1103639-(-1042151))Si[880785834%15728316]=P[Si[7504-7365]]Si[612425+-612286]=6033522-(-430431)<2590972624%15164252 Si[-516935-(-517076)]=S(Si[-1028194-(-1028336)],Si[454681+-454538])Si[2662369895%11329233]=P[Si[2501297247%16242189]]Si[-789917+790058]=-377903+4146792<9298046-209106 Si[645472-645329]=S(Si[680770182%11943334],Si[-167432+167577])Si[384796334%4372684]=P[Si[885909+-885766]]Si[1004001+-1003858]=15045181-883314~=736844+3213102 Si[1017153+-1017008]=S(Si[-726918-(-727064)],Si[-963956-(-964103)])Si[77701950%8633534]=P[Si[972747+-972602]]Si[678382-678235]=S(Si[-1016125-(-1016273)],Si[-999353+999502])Si[2194473055%10449871]=2138837982%23892492>=7402723-(-597493)Si[2046152243%14511717]=P[Si[873637989%12661418]]Si[476342189%14010060]=S(Si[1668118050%11120786],Si[-651205+651356])Si[3357475317%15987977]=5203446282%20605981~=984380+3485406 Si[-589314-(-589462)]=P[Si[115407905%12823084]]Si[1760078476%12482825]=S(Si[-1020455+1020607],Si[941851433%5091088])Si[1596383267%14127284],Si[754809+-754660]=1021238+8446442813991,1895875240%13318388<-999110+8522397 Si[-268561+268711]=P[Si[833115352%3804179]]Si[643866+-643715]=919600+7718130~=369552874%19624915 Si[271135538%3046465]=S(Si[-115875-(-116029)],Si[-767102+767257])Si[-359549-(-359701)]=P[Si[658334853%6583347]]Si[-1003571+1003724]=2762050145%13486456<=16255783-(-269434)Si[108331400%1217205]=S(Si[-890248-(-890404)],Si[1035356-1035199])Si[878124+-877970]=P[Si[-364007+364162]]Si[501919586%8507109]=1834129619%13243421<=3649522869%17847420 Si[258768557%1176220]=S(Si[-109077+109235],Si[1671136743%16068621])Si[395860+-395704]=P[Si[-470749+470906]]Si[288869881%7406916]=10900494-219172<806183+11611895 Si[477154+-476995]=S(Si[136382152%903192],Si[724443584%14204773])Si[146987-146829]=P[Si[-555753+555912]]Si[326349663%1326624],Si[228288+-228117]=2535523981%16513528~=10006232-203504,403550+18350879619331 Si[838162993%4029629]=S(Si[938185350%14002764],Si[540355+-540192])Si[470816+-470656]=P[Si[206856603%936002]]Si[63834-63665]=44947+1848209069001 Si[1411595719%15016974]=S(Si[443856-443692],Si[-54110-(-54275)])Si[321650+-321489]=1023638+14929570>1214801905%10248900 Si[933931395%7239777]=P[Si[622870917%5821222]]Si[-756834-(-756997)]=2049167817%25106962>=4019229632%17145559 Si[-604158+604323]=S(Si[2600291481%16776073],Si[69506-69339])Si[511891067%8676117]=P[Si[608488+-608323]]Si[-859768+859933]=1706775802%8608315<=1489114006%17586679 Si[843589+-843422]=S(Si[-269120+269288],Si[69608-69439])Si[-716647+716813]=P[Si[-385263+385430]]Si[559118+-558949]=S(Si[924120+-923950],Si[-552289+552460])Si[165523038%871173]=P[Si[-234953-(-235122)]]Si[345149-344980]=1206178267%13087509<=3192138-386298 Si[84310539%14051728]=S(Si[-185266+185438],Si[150931347%3971873])Si[-926649+926816]=-788457+8724844~=-733269+9503205 Si[-834845+835015]=P[Si[66201035%8275108]]Si[797166+-796995]=3788284-235106<=12117808-740154 Si[-1032897+1033070]=S(Si[1003934+-1003760],Si[2204816217%15418294])Si[372949642%1468305]=P[Si[-45049+45222]]Si[346407383%12371686]=S(Si[425308136%4725644],Si[513719+-513542])Si[-629392-(-629565)]=959415+12265482~=309137+11796296 Si[133176-133002]=P[Si[149131-148956]]Si[-917031-(-917206)]=2425085338%10125321<=11353834-521723 Si[2882653503%15252134]=S(Si[-73739-(-73917)],Si[896225-896046])Si[1628526296%13571051]=P[Si[-311267-(-311444)]]Si[-703916-(-704093)]=6298918-884998~=5655008-(-747221)Si[-344762+344941]=S(Si[611935233%3044453],Si[799816+-799635])Si[1630364148%14177078]=P[Si[879123-878944]]Si[1771752144%12746417]=S(Si[220820-220638],Si[-517320-(-517503)])Si[-985754-(-985933)]=76187+2302762~=-638223+14976839 Si[-516559+516739]=P[Si[-226684-(-226865)]]Si[-914834+915017]=S(Si[2276699704%11857810],Si[447676+-447491])Si[2698649146%11151442]=P[Si[1618507403%7356851]]Si[848902+-848721]=2722540569%17577222<6120679748%31959234 Si[393313+-393128]=S(Si[164902-164716],Si[708765+-708578])Si[-673166-(-673349)]=128158-(-402896)<5218918-738005 Si[-890974+891158]=P[Si[-922762+922947]]Si[-371880-(-372065)]=246854008%15732664>600156+7433935 v={[C]=Z,[r]=L,[s]=i,[p]=U;[q]=M;[D]=J;[V]=X,[F]=e,[Y]=c;[G]=E;[T]=hY;[mY]=QY;[kY]=dY;[uY]=oY;[jY]=aY;[KY]=HY,[NY]=SY,[PY]=gY,[tY]=yY;[BY]=bY,[WY]=fY,[RY]=vY,[CY]=ZY,[rY]=sY,[pY]=iY,[LY]=UY,[zY]=qY;[lY]=wY;[nY]=OY;[DY]=MY;[JY]=VY;[XY]=FY,[IY]=eY;[AY]=YY;[GY]=EY;[cY]=xY;[TY]=hi;[mi]=Qi;[ki]=di,[ui]=oi;[ji]=ai;[Ki]=Hi;[Ni]=Si[-86443+86444],[Si[-361071+361073]]=Si[1152003219%5538477];[Si[195969440%7537286]]=Si[312564+-312559];[Si[429328-429322]]=Si[2820746132%12003175],[Si[188149+-188141]]=Si[664596-664587];[Si[-762009+762019]]=Si[685683-685672];[Si[299588-299576]]=Si[-877198-(-877211)],[Si[203247-203233]]=Si[-579469-(-579484)];[Si[761682+-761666]]=Si[-925007+925024];[Si[-20007+20025]]=Si[769339-769320];[Si[448121410%2185958]]=Si[980266-980245];[Si[143992759%4644927]]=Si[-528923+528946];[Si[227096-227072]]=Si[-53181+53206];[Si[930581892%7886287]]=Si[-277831+277858];[Si[693082-693054]]=Si[504724799%13641210],[Si[-209481+209511]]=Si[-650279-(-650310)];[Si[-925800-(-925832)]]=Si[80338-80305];[Si[813059+-813025]]=Si[2134832770%8713603],[Si[-271354+271390]]=Si[-739102-(-739139)],[Si[2069681096%13016862]]=Si[-425283-(-425322)],[Si[1088564545%10367281]]=Si[806648-806607],[Si[239023255%14060189]]=Si[238199030%1517191],[Si[729297-729253]]=Si[-962877-(-962922)],[Si[-78789-(-78835)]]=Si[-84161-(-84208)],[Si[237037+-236989]]=Si[2168222543%12533078];[Si[970289231%10433217]]=Si[218208258%10390867];[Si[670590-670538]]=Si[1799773633%16361578],[Si[493373944%2442445]]=Si[-564158+564213],[Si[-872453-(-872509)]]=Si[692819-692762],[Si[-70919+70977]]=Si[750702440%9044607];[Si[86942-86882]]=Si[671796+-671735];[Si[234067+-234005]]=Si[-601193+601256],[Si[957464-957400]]=Si[1001462-1001397],[Si[-626133+626199]]=Si[340945057%11364833],[Si[1287076730%5385258]]=Si[-743882+743951],[Si[138165790%661080]]=Si[985296234%4951237],[Si[-997793-(-997865)]]=Si[-565447-(-565520)];[Si[997319726%4374209]]=Si[-833376-(-833451)];[Si[139785+-139709]]=Si[839921-839844],[Si[-459309-(-459387)]]=Si[-395380-(-395459)];[Si[-89307-(-89387)]]=Si[398713-398632];[Si[208369-208287]]=Si[184755-184672];[Si[485306754%4220058]]=Si[446411908%13527631],[Si[3445325486%13511080]]=Si[1032424-1032337],[Si[-94188+94276]]=Si[-540905+540994];[Si[-876463-(-876553)]]=Si[-172775-(-172866)];[Si[1410038688%11371279]]=Si[-187976+188069],[Si[437813554%6949420]]=Si[877661-877566];[Si[-1035861-(-1035957)]]=Si[938084-937987];[Si[-948175+948273]]=Si[-851339-(-851438)],[Si[-915259+915359]]=Si[-137312-(-137413)];[Si[343710+-343608]]=Si[558412465%16423893];[Si[-286074-(-286178)]]=Si[3900860832%16321593];[Si[-711324+711430]]=Si[681141+-681034],[Si[-949051-(-949159)]]=Si[-223921+224030],[Si[786288+-786178]]=Si[-435517+435628],[Si[368495517%3878899]]=Si[-447482-(-447595)];[Si[243064+-242950]]=Si[1660452265%11069681],[Si[1349959883%8490313]]=Si[2324144737%16601033],[Si[2184403318%13652520]]=Si[-282119+282238],[Si[139964304%818504]]=Si[137522+-137401];[Si[887156+-887034]]=Si[410619+-410496],[Si[1613201624%6452806]]=Si[370843+-370718],[Si[-822371+822497]]=Si[1698053649%8124658],[Si[779159818%10529185]]=Si[372051612%7915989],[Si[376170+-376040]]=Si[556871757%2554457];[Si[177205-177073]]=Si[2459466377%10882594],[Si[705886838%14705973]]=Si[-32162+32297],[Si[863509510%13706498]]=Si[424440857%3537006];[Si[988399-988261]]=Si[841715+-841576];[Si[146812-146672]]=Si[912630957%10995552];[Si[1636667334%9979678]]=Si[-169505-(-169648)],[Si[1194664464%9955536]]=Si[504070-503925],[Si[202420553%9639067]]=Si[-886297+886444],[Si[3869224650%15988531]]=Si[-744298+744447];[Si[-187050-(-187200)]]=Si[524490+-524339],[Si[3975409759%16633513]]=Si[15832264%15832111];[Si[199170+-199016]]=Si[1202355515%8906336];[Si[-920831+920987]]=Si[-236637-(-236794)];[Si[-391262-(-391420)]]=Si[-729317+729476],[Si[662682558%2932223]]=Si[-338911+339072],[Si[-956409+956571]]=Si[133509007%1059594],[Si[-235861+236025]]=Si[103802277%4325088],[Si[-856388-(-856554)]]=Si[-430630+430797];[Si[345130152%1797552]]=Si[-866618+866787],[Si[1232091866%9334028]]=Si[241351+-241180];[Si[73363+-73191]]=Si[-598906+599079];[Si[-120826+121000]]=Si[522609-522434],[Si[543324496%3087070]]=Si[194940207%1120345];[Si[1105872114%5316692]]=Si[-845031-(-845210)],[Si[-1029459-(-1029639)]]=Si[-514144-(-514325)],[Si[1402435398%6742477]]=Si[-966369+966552];[Si[-523693-(-523877)]]=Si[1867689671%15963158]}r,L,KY=m(-778053+716566),4746456512525-(-135317),m(-97349-(-35917))y[g]=v D,p,y,s,aY,jY=m(-77582+16144),m(618552+-680150),m(127511-189033),m(893556-955093),31312529598999-(-937694),m(231159-292577)g=h[y]uY=m(179617+-241148)y=g()Z,U,C,M,mY=148616+3289051742579,11139+2752548772222,m(284969+-346590),2459611754682-(-955327),m(171949+-233442)v=S(C,Z)Y,SY=m(945086-1006528),-615983+35106931877386 g=P[v]q,c,F=m(-858290-(-796859)),20171856622571-675642,m(-229097-(-167673))Z=S(r,L)G,e=m(-232491+171056),-912768+28839831331317 C=P[Z]Z,hY,i=5763053-266400~=731810+15809625,1827434117026-(-609200),18303265395517-733682 L=S(s,i)yY=-741399+26644908720270 r=P[L]i=S(p,U)L,kY,V=553330+9261306>622021-(-392311),m(808330-869775),m(381241+-442688)s=P[i]i=3563501-(-739663)~=2889302936%24796545 U=S(q,M)J=446472+7200660258065 p=P[U]NY,X,U=m(-445044+383625),501813+16234789123410,9011326-(-1043104)>=-1020801+8542401 M=S(D,J)q=P[M]QY,M=196642+5552344533495,-1037403+6280126~=127270555%3166866 J=S(V,X)D=P[J]J=-173900+12710349>696494414%6705143 X=S(F,e)E=26584637399993-144222 V=P[X]e=S(Y,c)dY,X=35184145539662-(-351665),-325699+2383661>=2424501176%14424803 F=P[e]c=S(G,E)e,oY=2746841-864347<443270+4994165,7189174553884-688137 Y=P[c]c,T=10792552-(-418395)~=784973+7396249,m(-931568-(-870104))E=S(T,hY)G=P[E]vY,RY,E=20300366814330-505741,m(-826920-(-765414)),8660563-(-711942)<793793+12630151 hY=S(mY,QY)T=P[hY]BY,hY=m(466816-528444),-260569+14366922>=489246-(-642583)QY=S(kY,dY)mY=P[QY]QY=12374084-155310>338254-(-442100)dY=S(uY,oY)kY=P[dY]oY=S(jY,aY)tY,HY,dY=m(210612-272194),4414529828576-290521,1005716562%5886731~=908993735%14615410 uY=P[oY]oY,PY=11404379-775640>5102990-382182,m(-602904-(-541482))aY=S(KY,HY)jY=P[aY]HY=S(NY,SY)aY,NY=-947305-(-984370)<=-66302+12899609,m(883610-945126)KY=P[HY]HY=7560648-708546>=42129+195272 v={[C]=Z;[r]=L;[s]=i;[p]=U,[q]=M,[D]=J,[V]=X,[F]=e;[Y]=c,[G]=E,[T]=hY,[mY]=QY,[kY]=dY;[uY]=oY,[jY]=aY;[KY]=HY}i,HY,c,L,T,e,mY=198180+2544843193981,24185295808377-539515,13781374476185-(-342392),30629399099765-573887,m(-693215-(-631795)),5739679851105-481265,m(97437+-158871)y[g]=v M,C,y,p,Y,r=32477607071774-(-568053),m(679344-740846),m(758622-820144),m(-477181-(-415733)),m(-225951+164383),m(823745-885378)g=h[y]dY,aY,F,jY=19438838533581-(-71054),15923596804278-(-154689),m(203148-264581),m(-239796+178266)y=g()E,fY,Z=-596387+32124270941202,-574387+34910935958323,1901981768204-(-158057)v=S(C,Z)g=P[v]s,q=m(799180+-860715),m(886170+-947796)Z=S(r,L)hY,U=505398+28840458747455,146422678322-(-916754)C=P[Z]J,Z,SY,D=-64293+20895723479335,3255454231%18454457<=11455381-589242,64694+3505773005226,m(161658+-223200)L=S(s,i)G=m(395190+-456783)r=P[L]X,uY=-860125+6346285771624,m(-229896+168386)i=S(p,U)oY=-651174+20386881164475 s=P[i]i,V,L=862445-(-67192)>=664833-89260,m(997786+-1059405),-648038+14172968>-943002+7443609 U=S(q,M)p=P[U]QY=12634544724436-(-343335)M=S(D,J)gY,U=3.9966952613687e+15%18676146082676,7069692533%27885551~=4558034-281414 q=P[M]J=S(V,X)M=6456613-(-252991)<=645794+10263128 D=P[J]J,WY=9062933-457204>=-874552+9227036,m(142990+-204474)X=S(F,e)V=P[X]e=S(Y,c)X=4396823983%21482283>=13056036-(-443595)F=P[e]KY,e=m(116693+-178121),5588424635%23836611>=10309960-294764 c=S(G,E)Y=P[c]c=1764464628%9839017~=1439420884%19912725 E=S(T,hY)kY=m(-241537-(-180116))G=P[E]E,ZY=1757247762%21576613>=812807+8351276,30878290656300-934914 hY=S(mY,QY)T=P[hY]QY=S(kY,dY)mY=P[QY]hY,QY=6856055580%27033150>=66048-(-926548),-181291+7436625>720964924%17037587 dY=S(uY,oY)kY=P[dY]dY=1563432029%11868121~=-925534+11214231 oY=S(jY,aY)uY=P[oY]aY=S(KY,HY)jY=P[aY]bY=10706434558438-783981 HY=S(NY,SY)oY,aY=8411600-(-1835)>=-899824+2730001,10217149-846676<596086+9867887 KY=P[HY]SY=S(PY,gY)NY=P[SY]SY=787695+5187712~=-70419+8126727 gY=S(tY,yY)PY=P[gY]gY,CY,HY=-264550+1131683<=16642895-(-6002),m(-966603+905032),1276898960%12221237<=7978416-(-166253)yY=S(BY,bY)tY=P[yY]bY=S(WY,fY)yY=720370439%10878296>2648070-641781 BY=P[bY]fY=S(RY,vY)bY=587730693%19949768<1071132123%21984318 WY=P[fY]vY=S(CY,ZY)RY=P[vY]fY,vY=-865324+12217266<=6783370673%30080720,1955093382%10234712<1316331286%26122219 v={[C]=Z;[r]=L,[s]=i,[p]=U,[q]=M;[D]=J,[V]=X;[F]=e,[Y]=c;[G]=E;[T]=hY;[mY]=QY,[kY]=dY;[uY]=oY,[jY]=aY;[KY]=HY;[NY]=SY,[PY]=gY;[tY]=yY,[BY]=bY,[WY]=fY,[RY]=vY}s,L=26311201398046-863554,m(-973029+911484)y[g]=v y=m(-884026-(-822395))g=h[y]C=m(-1035544-(-973998))v=h[C]r=S(L,s)Z=P[r]r,S,P=m(-169215+107656),nil,nil r=v[r]C={r(v,Z)}y=g(k(C))g=y()else S=K[u[1005407-1005404]]P=595618+-595586 H=S%P v=K[u[-171046-(-171049)]]P=-88112-(-88125)y=v-H v=1245885816%7243522 g=y/v Q=4391603553%17596240 S=P-g L=-647172-(-647174)y=K[u[-434666-(-434670)]]Z=K[u[175563877%7022555]]r=L^S S=nil C=Z/r v=y(C)y,r=1012803+4293954493,975820-975819 g=v%y v=-963662+963664 y=v^H P=g/y y=K[u[-937149-(-937153)]]Z=P%r r=4294224735-(-742561)C=Z*r v=y(C)y=K[u[599140-599136]]C=y(P)g=v+C i=518215+-517959 U,v=-784149+784405,-1964+67500 y=g%v Z,r=-585501-(-651037),-672168+672424 C=g-y v=C/Z Z=y%r s=y%i P=nil L=y-s s=329648386%3662757 r=L/s s=267015+-266759 L=v%s p=v%U H=nil i=v-p y,v,p=nil,nil,25820-25564 s=i/p C={Z,r,L,s}K[u[2258691%322670]]=C g=nil end end end else if Q>15079451-(-183696)then if Q<2713170809%23448359 then if Q<16553846-864243 then s,Q=m(-659003-(-597491)),-134442+9925127 L=h[s]a=L elseif Q<5097863435%20998973 then Q,i=748896+15949467,p M=i s[i]=M i=nil else O=N()D,V=m(-557095-(-495496)),-253763+254018 K[O]=z e=m(894098-955594)M=h[D]D,J=m(-814438+752971),44149050%8829790 a=M[D]D=-895444+895445 M=a(D,J)J=-743409-(-743409)D=N()K[D]=M G=608161-608161 a=K[C]M=a(J,V)J=N()V,E=607129-607128,468770842%2416293 K[J]=M a=K[C]I=116764533%8981887 X=K[D]F=-694006+694007 M=a(V,X)V=N()K[V]=M M=K[C]X=M(F,I)M=317816-317815 a=X==M M=N()K[M]=a X=m(-689234-(-627598))A=h[e]Y=K[C]c={Y(G,E)}a,I=m(234424-296001),m(-908253+846721)a=U[a]e=A(k(c))A=m(-760034-(-698502))x=e..A F=I..x a=a(U,X,F)X=N()I=m(-961640+900123)x=f(1567060763%13874281,{C,O,s;P,S;q,M,X;D,V;J;r})K[X]=a F=h[I]I={F(x)}a={k(I)}F=a a=K[M]Q=a and 14568472-697583 or 2989437-(-793672)end else if Q<-401271+17098500 then s=s+i r,U=L>=s,not p r=U and r U=L<=s U=p and U r=U or r U=845483562%9383315 Q=r and U r=1802326411%7899476 Q=Q or r else M,p=not O,p+q i=p<=U i=M and i M=p>=U M=O and M i=M or i M=894276+14806711 Q=i and M i=995367513%13942572 Q=Q or i end end else if Q>1588710702%19196220 then if Q<-288904+15072971 then Q=8607567-(-325310)else n=313009+11022586~=15593563-424107 Q=n and 2022507024%19721043 or-861912+6117032 end else if Q<2256664684%22655535 then Q,a=h[m(-979184+917745)],{S}elseif 236828+13959249>Q then x=K[S]a,I=x,Q Q=x and-739916+5619211 or 5236902-(-755803)else r=W(406151+11690319,{})g,a=m(-828575-(-767079)),m(-910904-(-849279))Q=h[a]Z=m(-387149+325632)H=K[u[680223100%9192204]]P=h[g]C=h[Z]Z={C(r)}C,v=506508209%4563137,{k(Z)}y=v[C]g=P(y)P=m(-691948-(-630312))S=H(g,P)H={S()}a=Q(k(H))S=K[u[855953192%3437563]]H=a a,Q=S,S and 650462+213703 or 336367676%14585713 end end end end else if 4984939858%24746784>Q then if Q<9822974-(-142265)then if 998610066%20618204>Q then if 2377733032%19420845>Q then H,S=d[-510825-(-510826)],d[2012377313%10647499]Q=K[u[27421+-27420]]P=Q Q=P[S]Q=Q and 640116+13022434 or 3031698601%17220937 elseif Q<9076577-329021 then a,Q={S},h[m(-797652-(-736048))]else Q=485615+13395705>4697970-(-863327)K[S]=Q Q=4692322300%18648741 end else if Q<-727793+9856643 then Q=23755918%11755659 elseif 9946468-392112>Q then a,Q={},h[m(-920668-(-859124))]else Q=r r=N()z=b(934562332%5637022,{})K[r]=a U,s,i,l=m(730177+-791694),-720074-(-720077),-743162-(-743227),m(697756+-759252)a=K[C]L=a(s,i)a=1011911-1011911 s=N()K[s]=L p=h[U]L=a a=386343591%1658127 U={p(z)}z,i=m(-584551+522926),a a={k(U)}U,p=820788-820786,a a=p[U]U=a a=h[z]q=K[P]w=h[l]l=w(U)w=m(484677+-546313)n=q(l,w)q={n()}z=a(k(q))a=-318877+318878 q=N()K[q]=z Q=11252723-537884 z=K[s]n=z z=3576142837%15684837 w=z z=1293495737%5648453 l=w<z z=a-w end end else if-589898+10988415>Q then if 344279+9835168>Q then S=K[u[-616101-(-616102)]]H=#S P=K[u[479447+-479446]]S=P[H]g=nil P=K[u[1198935277%9082843]]P[H]=g Q=h[m(-606622+545071)]a={S}elseif 10347538-100452>Q then C,P=not v,P+y a=g>=P a=C and a C=P>=g C=v and C a=C or a C=11547290-1025327 Q=a and C a=354218866%14867794 Q=Q or a else c=-364012+364014 Y=F[c]c=K[X]e=Y==c x,Q=e,-437440+2278449 end else if Q<629327+9989074 then a,C=-770696-(-770696),P Q=C==a Q=Q and 5268386-952188 or 557418+10400291 else z,O=w+z,not l a=n>=z a=O and a O=n<=z O=l and O a=O or a O=-132772+16655724 Q=a and O a=6183139-508365 Q=Q or a end end end else if Q<3023736519%22148348 then if 12050501-647348>Q then if 10023753-(-935420)>Q then Z=807136-807135 a=C==Z Q=a and 4097949-940460 or 369092+11119217 elseif Q<4184129934%26245224 then n=K[C]O,l=48365-48359,600190-600189 w=n(l,O)O,n=m(851623-913235),m(-806344-(-744732))h[n]=w l=h[O]O=954369344%8597922 n=l>O Q=n and 4782850774%20388910 or-486858+7105827 else e,Q=999891+-999890,12454736-(-669447)A=F[e]I=A end else if Q<976095+10523692 then C,Q=nil,3348731808%14970909 else Q=-434783+3618277<15773680-(-741195)Q=Q and 613073755%5339503 or 965690912%18287901 end end else if 12174572-216372>Q then if 997106+10672721>Q then C,P=not v,P+y S=P<=g S=C and S C=P>=g C=v and C S=C or S C=693061461%14905142 Q=S and C S=2582805-584450 Q=Q or S elseif 11720389-(-66797)>Q then Q=13035470-203056 else l,M=m(347021-408517),m(726374+-787800)n=h[l]O=h[M]l=n(O)n=m(176442+-238054)h[n]=l Q=407050713%14423014 end else if 12155009-71491>Q then w=L==i Q,z=1812535228%10397551,w else a,P,S=7828117-(-739772),868810+3055242,m(-563433+501858)H=S^P Q=a-H H,a=Q,m(-852960+791434)Q=a/H a={Q}Q=h[m(308199-369698)]end end end end end end end Q=#o return k(a)end,function(h,m)local k=P(m)local d=function(d)return Q(h,{d},m,k)end return d end,function(h)for m=437428664%15083747,#h,-319647-(-319648)do H[h[m]]=2145395267%13664938+H[h[m]]end if d then local Q=d(true)local k=o(Q)k[m(843417-905009)],k[m(-313565+252110)],k[m(830933-892542)]=h,g,function()return-503312+-779173 end return Q else return u({},{[m(-631806-(-570351))]=g,[m(111074-172666)]=h;[m(667252+-728861)]=function()return-2017148-(-734663)end})end end,function(h,m)local k=P(m)local d=function(d,u,o,j)return Q(h,{d,u,o,j},m,k)end return d end return(y(2566842411%18312464,{}))(k(a))end)(select,getfenv and getfenv()or _ENV,setmetatable,getmetatable,{...},unpack or table[m(110927+-172439)],newproxy)end)(...)
