//
// This Stan program defines a simple model, with a
// vector of values 'y' modeled as normally distributed
// with mean 'mu' and standard deviation 'sigma'.
//
// Learn more about model development with Stan at:
//
//    http://mc-stan.org/users/interfaces/rstan.html
//    https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started
//

// The input data is a vector 'y' of length 'N'.
data {
  int<lower=1> n;
  int<lower=1> q;
  int<lower=0, upper=1> y[n];
  matrix[n,q] x;
  vector[q] m_beta;
  matrix[q,q] s_beta;
}

// The parameters accepted by the model. Our model
// accepts two parameters 'mu' and 'sigma'.
parameters {
  vector[q] beta;
  
}

transformed parameters{
  
  vector[n] theta;
  for(i in 1:n){
    theta[i] = exp(x[i,]*beta) / (1 + exp(x[i,]*beta));
  }
  
}

// The model to be estimated. We model the output
// 'y' to be normally distributed with mean 'mu'
// and standard deviation 'sigma'.
model {
  
  for(i in 1:n){
    y[i] ~ bernoulli(theta[i]);
  }
  
  beta ~ multi_normal(m_beta, s_beta);
  
}


