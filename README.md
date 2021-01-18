# Exercise-answer-about-Lexical-via-R-Programming

1.makeCacheMatrix:
This function creates a special "matrix" object that can cache its inverse.

makeCacheMatrix <- function(x=matrix(),...){
       m<-NULL
       set<-function(y){
               x<<-y #用<<-可以可以使起在赋值行为均在environment hierarchy上进行
               m<<-NULL
       }
       get<-function() x
       setM<-function(solve) m<<-solve
       getM<-function() m
       list(set=set,get=get,setM=setM,getM=getM)
}

2.cacheSolve:
This function computes the inverse of the special "matrix" returned by makeCacheMatrix above. If the inverse has already been calculated (and the matrix has not changed), then the cachesolve should retrieve the inverse from the cache.

cacheSolve <- function(x, ...) {
  m <- x$getM()
  if(!is.null(m)){
    message("TO cached data")
    return(m)
  }
  data <- x$get()
  m <- solve(data,...)
  x$setM(m)
  m
  }
