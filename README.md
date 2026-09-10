# EXP 5 : Multirate Signal Processing- Decimation and Interpolation
#          Multirate Signal Processing- Decimation and Interpolation
# AIM: 
          
  To perform decimation and interpolation operations on a discrete time signal and study the spectrum using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM for Decimation
```
clc;
clear;
close;

// Parameters
Fs = 1000;
f = 50;
N = 100;

// Original signal
t = (0:N-1)/Fs;
x = sin(2*%pi*f*t);

// Add noise
noise = 0.4 * rand(1,N,"normal");
xn = x + noise;

// Interpolation
L = 2;
xi = zeros(1,L*N);

for i = 1:N
    xi((i-1)*L+1) = xn(i);
end

Fsi = L*Fs;
ti = (0:length(xi)-1)/Fsi;

// Decimation
M = 2;
xd = xi(1:M:length(xi));

Fsd = Fsi/M;
td = (0:length(xd)-1)/Fsd;

// Frequency response
X = fft(xn);
faxis = (0:N-1)*Fs/N;
Xmag = abs(X)/N;

// ---------------- 2 x 2 DISPLAY ----------------
figure(1);

// 1. Original Signal
subplot(2,2,1);
plot(t,x);
xtitle("Original Signal","Time (s)","Amplitude");
xgrid();

// 2. Noisy Signal
subplot(2,2,2);
plot(t,xn);
xtitle("Noisy Signal","Time (s)","Amplitude");
xgrid();

// 3. Frequency Response
subplot(2,2,3);
plot(faxis,Xmag);
xtitle("Frequency Response","Frequency (Hz)","Magnitude");
xgrid();

// 4. Interpolated Signal
subplot(2,2,4);
plot(ti,xi);
xtitle("Interpolated Signal","Time (s)","Amplitude");
xgrid();

// ---------------- DECIMATED SIGNAL ----------------
figure(2);
plot(td,xd);
xtitle("Decimated Signal","Time (s)","Amplitude");
xgrid();

```
# PROGRAM for Interpolation

# OUTPUT and spectrum for Decimation

<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/998e48d7-90d0-4df1-a950-710ab92a2890" />

# OUTPUT and spectrum for Interpolation

<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/30c61b6f-69d5-4c57-a077-55d72829acb1" />

# RESULT

Thus the program for decimation and interpolation operations on a discrete time signal is successfully done using SCILAB.
