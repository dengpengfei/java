import java.util.Arrays;
import java.util.List;

public class T {
    public static void main(String[] args) {

        System.out.println("ok");

        //                                 1    2    3    4    5    6    7    8    9    10   11   12
        List<String> list = Arrays.asList(" ", "N", "N", "N", "N", "N", "N", "Y", " ", " ", " ", " ");


        //List<String> list = Arrays.asList(" ", " ", " ", " ", " ", "Y", "Y", "N", " ", " ", " ", " ");

        int month = 9;

        int startMonth = month - 2;
        int mIndex = -1;
        for (mIndex = startMonth - 1; mIndex >= 0; ) {

            String curValue = list.get(mIndex);
            System.out.println("当前位置：【" + (mIndex) + "】 value=" + curValue);
            if (curValue.equals(" ")) {
                System.out.println("当前没有提交答案， 从当前开始答题:" + mIndex);
                break;
            } else if (curValue.equals("Y")) {
                int nextIndex = mIndex + 1;
                String nextValue = list.get(nextIndex);
                if (nextValue.equals(" ")) {
                    System.out.println("当前没有提交答案， 从当前开始答题[back]" + nextIndex);
                    break;
                } else if (nextValue.equals("Y")) {
                    mIndex = month - 1;
                    System.out.println("向前遍历结束， 开始答中间的题中间开始:" + mIndex);
                    break;
                } else {
                    //N
                    mIndex--;
                    System.out.println("向前1步:" + (mIndex));
                    continue;
                }

            } else {
                //N
                mIndex = mIndex - 2;
                System.out.println("向前2步:" + (mIndex));
                continue;
            }

        }

        //说明已经退出边界
        if (mIndex < 0) {
            //但是第一道题还没答
            if (list.get(0).equals(" ")) {
                //index = 1
                //return 0;
            }
        }

        //当前月龄
        if (mIndex == month) {
            //当前月龄还没答
            if (list.get(mIndex).equals(" ")) {
                //index = month
                //return 0;
            }
        }

        //向前，向中遍历完成， 开始向后遍历

        int backMonth = month + 1;
        int backIndex = -1;
        for (backIndex = backMonth - 1; backIndex < 72; ) {
            String curValue = list.get(backIndex);
            System.out.println("当前位置：【" + (backIndex) + "】 value=" + curValue);
            if (curValue.equals(" ")) {
                System.out.println("当前没有提交答案， 从当前开始答题:" + backIndex);
                break;
            } else if (curValue.equals("N")) {
                int nextIndex = mIndex + 1;
                String nextValue = list.get(nextIndex);
                if (nextValue.equals(" ")) {
                    System.out.println("当前没有提交答案， 从当前开始答题[back]" + nextIndex);
                    break;
                } else if (nextValue.equals("N")) {
                    mIndex = month - 1;
                    System.out.println("向后遍历结束" + mIndex);
                    break;
                } else {
                    //Y
                    mIndex++;
                    System.out.println("向前1步:" + (mIndex));
                    continue;
                }

            } else {
                //Y
                mIndex++;
                System.out.println("向后1步:" + (mIndex));
                continue;
            }
        }
    }
}
