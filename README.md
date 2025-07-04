# Ventures
Ventures, a cutting edge product pushing the limits of external memory modification.

# Lua Implementation
## Memory
```lua
local base = memory:get_base_address()
local datamodel = memory.read_pointer(base + 0x12345)
local placeid = memory.read_int(datamodel + 0x123)
local fps = memory.read_float(datamodel + 0x50)
local place_name = memory.read_string(datamodel + 0x12)
local position = memory.read_vector3(datamodel + 0x22)
local cf = memory.read_cframe(datamodel + 0x12)
local aobscan = memory.pattern_scan("00 11 22 33 44")
-- note, writing is nearly the same!

memory.write_pointer(base + 0x12345, 0x20)
memory.write_int(datamodel + 0x123, 67)
memory.write_float(datamodel + 0x50, 20)
memory.write_string(datamodel + 0x12, "mustard!!!")
memory.write_vector3(datamodel + 0x22, Vector3.new(12,12,12))
memory.write_cframe(datamodel + 0x12, CFrame.new(1,1,1))
```
## GUI
```lua
local library = gui_service:initialize({
  Name = "Tutorial!",
  Size = Vector2.new(400,400),
  Visible = true,
  Watermark = "None" -- Set as "None" for no watermark!
})
local tab1 = library:addtab("aimbot", Icon = "https://cdn-icons-png.flaticon.com/512/3082/3082985.png")

local sections = tab1:add_sections(2) -- add two sections

sections:next_section() -- go to first

tab1:header("this is a header!")

tab1:text("This is a section!")

sections:next_section()

tab1:button("This is a button!", function()
  print("clicked!")
end)

tab1:dropdown("select a option", options = {"hi","bye"}, multi = false, callback = function(option)
  print(option)
end)

tab1:dropdown("select many options", options = {"hi","bye", "hello"}, multi = true, callback = function(options)
  for _, option in pairs(options) do
    print(option)
  end
end)

tab1:toggle("hi", function(bool)
  if bool then
    print("hi!")
  else
    print("bye")
  end
end)

tab1:add_slider("this is a slider!", 1, 100, 0.5, function(value) -- 1 is min, 100 is max, 0.5 is interval
  print(value)
end)
-- edit gui elements/themes --
library.back_color = Color3.fromRGB(255,255,255)
library.tabs_color = Color3.fromRGB(255,0,0)
library.title_color = Color3.fromRGB(1,1,1)
library.primary_color = Color3.fromRGB(0,255,0)
library:set_back_image("https://www.mustard.com")
library.tab_padding = 2
library.transparency = 0
```
## Drawing
```lua
local line = Drawing.new("Line")
line.to = Vector2.new(1,1)
line.from = Vector2.new(2,2)
line.thickness = 5
line.transparency = 0
line.visible = true
line.color = Color3.fromRGB(255,255,255)

local box = Drawing.new("Square")
box.size = Vector2.new(12,12)
box.thickness = 5
box.transparency = 0
box.visible = true
box.position = Vector2.new(55,55)
box.color = Color3.fromRGB(255,255,255)

local circle = Drawing.new("Circle")
circle.radius = 15
circle.position = Vector2.new(12,12)
circle.transparency = 0
circle.visible = false
circle.thickness = 1
circle.color = Color3.fromRGB(255,255,255)

local triangle = Drawing.new("Triangle")
triangle.point_1 = Vector2.new(12,12)
triangle.point_2 = Vector2.new(1,12)
triangle.point_3 = Vector2.new(5,12)
triangle.transparency = 0
triangle.color = Color3.fromRGB(255,255,255)
triangle.thickness = 2
```
## Globals
```lua
local players = game.players
local workspace = game.workspace
local coregui = game.coregui
local replicatedstorage = game.replicatedstorage
```
## Files
```lua
-- example code below --

local config_folder = find_folder("configs")
if not config_folder then
  config_folder = make_folder("configs")
end
local config = find_file(config_folder, "config.cfg")
if not config then
  config = make_file(config_folder, "config.cfg", "nothing")
end
local data = read_file(config)
write_file(config, "hello!?")

for index, file in list_files(config_folder) do
  print(file)
end
-- note, you cannot save executable files.
```
