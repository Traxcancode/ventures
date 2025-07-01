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

-- note, writing is nearly the same!

memory.write_pointer(base + 0x12345, 0x20)
memory.write_int(datamodel + 0x123, 67)
memory.write_float(datamodel + 0x50, 20)
memory.write_string(datamodel + 0x12, "mustard!!!")
memory.write_vector3(datamodel + 0x22, Vector3.new(12,12,12))
memory.write_cframe(datamodel + 0x12, CFrame.new(1,1,1))
```
## GUI
```
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

library.back_color = Color3.fromRGB(255,255,255)
library.tabs_color = Color3.fromRGB(255,0,0)
library.title_color = Color3.fromRGB(1,1,1)
library.primary_color = Color3.fromRGB(0,255,0)
```
