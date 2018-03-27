<pre class="prettyprint lang-java linenums">public class StringSplit {
    public static void main(String[] args) {
        String sourceStr = "1,2,3,4,5";
        String[] sourceStrArray = sourceStr.split(",");
        for (int i = 0; i &lt; sourceStrArray.length; i++) {
            System.out.println(sourceStrArray[i]);
        }

        // 最多分割出3个字符串
        int maxSplit = 3;
        sourceStrArray = sourceStr.split(",", maxSplit);
        for (int i = 0; i &lt; sourceStrArray.length; i++) {
            System.out.println(sourceStrArray[i]);
        }
    }
}</pre>
<br />