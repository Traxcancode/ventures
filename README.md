# Ventures
Ventures, a cutting edge product pushing the limits of external memory modification.

# Luas
## Memory
```lua
local base = memory:GetBaseAddress()
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
