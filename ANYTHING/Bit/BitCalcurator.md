#kotlin 

    @Test
    fun `bit flag 계산`() {
        var flag = 0
        //flag on
        println("on =====================")
        flag = flag or 1
        flag = flag or 4
        println(flag)
        println(Integer.toBinaryString(flag))
        println(toBinary(flag, 4))

        if ((flag and 1) == 1) println("1 true")
        if ((flag and 2) == 2) println("2 true")
        if ((flag and 4) == 4) println("4 true")
        if ((flag and 8) == 8) println("8 true")

        //flag off
        println("off =====================")
        flag = flag and 4.inv()
        println(flag)

        //flag 반전
        println("반전 =====================")
        flag = flag xor 4
        println(flag)
        flag = flag xor 4
        println(flag)

    }
    fun toBinary(x: Int, len: Int): String {
        return String.format(
            "%" + len + "s",
            Integer.toBinaryString(x)
        ).replace(" ".toRegex(), "0")
    }

우선 저장.