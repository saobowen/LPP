# Locality Projection Reserved with Matlab
 
This Project used to re-code LPP of [XF.H@cad.zju](http://www.cad.zju.edu.cn/home/xiaofeihe/)

author: BW.C @zjut  
date: 2018/10/18  
intro:   
   * Step1. Construct W
       W is a sparse weight matrix of given point set x(x1,x2....xn). Constructing W can be broken into two questions:
       1) construct the adjacency graph G
   
       2) choose the weight W[i][i]  
   
       - for question 1:  
  
           1) ε-neighbours[ε belongs to R]  
                ```
               if (||x_i-x_j||^2<ε) (normal Euclidean norm)  
                   x_i  x_j connected
               else
                   x_i  x_j not connected
                ```
           2) k nearest neighbours 
                ```
               if (KNN)
                   x_i  x_j connected
               else
                   x_i  x_j not connected
                ```
                >KNN:i is among k nearest neighbours of x_j and j is among k nearest neighbours of x_i  

       - for question 2:  
           1) heat kernel  
               W[i][j]=e^(-(||x_i-x_j||)^2/t))  
                >refer to:[M.belkin and P.Niyougi,"Laplacian Eigenmaps abd Spectral Techniques..."](
                        url:http://web.cse.ohio-state.edu/~belkin.8/papers/LEM_NIPS_01.pdf)

           2) simple 0-1  
                ```
               if (x_i x_j connected)
                   W[i][j]=W[j][i]=1 (W is a symmetric matrix)
               else
                   W[i][j]=W[j][i]=0
                ```
