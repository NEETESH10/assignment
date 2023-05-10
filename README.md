# assignment
public class BestCoordinate {
    public static int[] bestCoordinate(int[][] towers, int radius) {
        int x_min = 50, x_max = 0, y_min = 50, y_max = 0, max = 0;
        int[] res = new int[2];
        for(int[] tower : towers) {
            x_min = Math.min(x_min, tower[0]);
            x_max = Math.max(x_max, tower[0]);
            y_min = Math.min(y_min, tower[1]);
            y_max = Math.max(y_max, tower[1]);
        }
        for(int i = x_min; i <= x_max; i++) {
            for(int j = y_min; j <= y_max; j++) {
                int sum = 0;
                for(int[] tower : towers) {
                    int dis = (tower[0] - i) *(tower[0] - i) + (tower[1] - j) *(tower[1] - j);
                    if(dis <= radius*radius) {
                        sum += tower[2]/(1 + Math.sqrt(dis));
                    }
                }
                if(sum > max) {
                    max = sum;
                    res = new int[]{i,j};
                }
            }
        }
        return res;
    }


    public static void main(String[] args){

        int n=3;
        int[][] towers = {{1,2,5},{2,1,7},{3,1,9}};
        int radius = 2;

        int[] ans = bestCoordinate(towers, radius);

        System.out.println("["+ans[0]+","+ans[1]+"]");


    }

}
