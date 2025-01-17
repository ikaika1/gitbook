---
description: These functions convert from hexadecimal to string and integer formats
---

# 💡 Hex Converters

## UDF\_HEX\_TO\_INT()

Converts from hexadecimal to integer. The number is returned as a string to avoid any big number limitations.

### Syntax

```sql
utils.udf_hex_to_int(
    [encoding,]
    hex
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert

**Optional:**

* `encoding` (string): The encoding to use. Valid values are `s2c` and `hex`. This parameter is optimal.&#x20;
  * Default: `hex`

### Sample Queries

```sql
-- These are all the same.
select
  utils.udf_hex_to_int ('1E240')::int as int1,
  utils.udf_hex_to_int ('0x1E240')::int as int2,
  utils.udf_hex_to_int ('hex','0x1E240')::int as int3;

-- Hex to Signed 2's Complement Integer. These are the same.
select
  livequery.utils.udf_hex_to_int ('s2c','FFFE1DC0')::int as int1,
  livequery.utils.udf_hex_to_int ('s2c','0xFFFE1DC0')::int as int2
```

## UDF\_INT\_TO\_HEX()

### Synatx

```
utils.udf_int_to_hex(
    int
)
```

### Arguments

**Required:**&#x20;

* `int` (integer): The integer to conver&#x20;

### Sample Query

```sql
select
  utils.udf_int_to_hex(123)::string as hex
```

## UDF\_HEX\_TO\_STRING()

Converts from hexadecimal to string. It will handle obscure chacaters like emojis and special characters.&#x20;

### Syntax

```
utils.udf_hex_to_string(
  hex
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert&#x20;

### Sample Query

```
select utils.udf_hex_to_string('4469616D6F6E642048616E6473') as text1;
```
