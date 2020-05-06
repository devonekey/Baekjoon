import java.util.Scanner

class Main {
    companion object {
        @JvmStatic
        fun main(args: Array<String>) = with(Scanner(System.`in`)) {
            val N = nextInt()
            val M = nextInt()
            val map = Array(N) {
                IntArray(M, init = { nextInt() })
            }
            val dp = Array(N, init = { IntArray(M) })

            dp[0][0] = map[0][0]

            for (i in 0 until N) {
                for (j in 0 until M) {
                    if (i != 0) {
                        dp[i][j] = Math.max(dp[i][j], map[i][j] + dp[i - 1][j])
                    }

                    if (j != 0) {
                        dp[i][j] = Math.max(dp[i][j], map[i][j] + dp[i][j - 1])
                    }
                }
            }

            dp.forEach {
                it.forEach {
                    print("$it, ")
                }
                println()
            }

            /*for (i in 1 until N) {
                for (j in M - 1 downTo 0) {
                    dp[i][j] = Math.max(dp[i][j], map[i][j] + dp[i - 1][j])
                    dp[i][j] = Math.max(dp[i][j], map[i][j] + dp[i][j - 1])
                }
            }*/
        }
    }
}