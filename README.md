# java-code
class Solution {
    public int trap(int[] height) {
        int n=height.length;
       int[] lmax=new int[n];
        lmax[0] = height[0];
//we start from 1 to check the left index side index
    for(int i=1;i<n;i++){
        int temp = Math.max(height[i], lmax[i-1]);
        lmax[i] = temp;
    }
    
    int[] rmax=new int[n]; 
	//we start from n-2  to check the right side index
        rmax[n-1] = height[n-1];
    for(int i=n-2; i>=0 ;i--){
//Math.max will check the max index from height[i] and rmax[i+1]
        int temp = Math.max(height[i], rmax[i+1]);
        rmax[i] = temp;
    }
    
    int water=0;
    for(int i=1;i<n-1;i++){
        water+= Math.min(lmax[i], rmax[i]) - height[i];
    }
    
    return water;
    }
}
class Main{
    public static void main (String[] args) {
        Solution s= new Solution();
        int[] height={0,1,0,2,1,0,1,3,2,1,2,1};
        
        int  output= s.trap( height) ;
        
            System.out.println(output);
        
    }
}
