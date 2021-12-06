# CRC32

```c++
  // creat crc table
static void init_crc_table(uint64_t *crc_tab32)
{
    int crc;
    for (int i = 0; i < 256; i++)
    {
        crc = i;
        for (int j = 0; j < 8; j++)
        {
            if (crc & 1)
                crc = (crc >> 1) ^ 0xEDB88320;
            else
                crc = crc >> 1;
        }
        crc_tab32[i] = crc;
    }
}

unit64_t getCRC(unsigned char* buf, int nLength)
{
    if (nLength < 1)
        return 0xffffffff;
    UINT32 crc = 0;
    for (int i(0); i != nLength; ++i)
    {
        crc = crc_tab32[(crc ^ buf[i]) & 0xff] ^ (crc >> 8);  
    }
    crc = crc ^ 0xffffffff;
    return crc;  
}
```

