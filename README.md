# MATLAB_CODE
%Set the sampling frequency and carrier frequency. 
%Generate a time vector.
fs = 100000; 
fc = 200;  
t = (0:1/fs:0.2)';
fDev =50;
%Create two-tone sinusoidal signal with frequencies 30 and 60 Hz.
x =sin(2*pi*30*t)+sin(2*pi*60*t);
%Set the frequency deviation to 50 Hz.
subplot(4,1,1);
plot(t,x);
xlabel('Time');
ylabel('Amplitude');
title('Message Signal');
grid on;
%.....Carrier signal.....
c=sin(2*pi*fc*t);
subplot(4,1,2);
plot(t,c);
xlabel('Time');
ylabel('Amplitude');
title('Carrier Signal');
grid on;
%Frequency modulate x.
y = 2.*fmmod(x,fc,fs,fDev);
%Demodulate z.
subplot(4,1,3);
plot(t,y);
xlabel('Time');
ylabel('Amplitude');
title('FM Signal');
grid on;
z = fmdemod(y,fc,fs,fDev);
%Plot the original and demodulated signals.
subplot(4,1,4);
plot(t,z);
xlabel('Time');
ylabel('Amplitude');
title('FM demodulation Signal');
grid on;
