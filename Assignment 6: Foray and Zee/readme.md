# Assignment 6: Foray and Zee

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%206%3A%20Foray%20and%20Zee/Assignment6.pdf)

## Solution
```matlab
% Assignment 6 (Talha Akhlaq) (3/24/2025) (ECE210-A) (Prof. Darius)

% Question 1:
dB2mag = @(dB) 10^(dB/20);

% Question 2:
Fs = 44100;
N = 88200;
t = (0:N-1)/Fs;
freqs = [14.96e3, 5.52e3, 3.15e3, -3.76e3, 11.01e3];
dbValues = [20, 19, 7, -7, -4];

x = zeros(1, N);
for i = 1:length(freqs)
    x = x + dB2mag(dbValues(i)) * exp(1j*2*pi*freqs(i)*t);
end
x = x + dB2mag(-10) * randn(1, N);

figure
subplot(2,1,1)
plot(t, real(x), 'LineWidth', 1)
grid on
xlabel('Time (s)')
ylabel('Amplitude')
title('Real Component of Signal')

X = fft(x);
fAxis = (0:N-1)*(Fs/N);
subplot(2,1,2)
plot(fAxis, abs(X), 'LineWidth', 1)
grid on
xlim([0 Fs/2])
xlabel('Frequency (Hz)')
ylabel('Magnitude')
title('DFT Magnitude')

% Question 3:
z_zeros = [
    0.55 + 1j*0.08
    0.55 - 1j*0.08
    0.39 + 1j*0.96
    0.39 - 1j*0.96
    0.07 + 1j*0.68
    0.07 - 1j*0.68
    0.08
];
z_poles = [
   -0.06 + 1j*0.83
   -0.06 - 1j*0.83
    0.30 + 1j*0.69
    0.30 - 1j*0.69
    0.77 + 1j*0.61
    0.77 - 1j*0.61
   -0.68
   -0.34
];

k = -0.43;
num = k * poly(z_zeros);
den = poly(z_poles);

figure
plot(real(z_zeros), imag(z_zeros), 'o', 'MarkerSize', 8, 'LineWidth', 1)
hold on
plot(real(z_poles), imag(z_poles), 'x', 'MarkerSize', 8, 'LineWidth', 1)
theta = linspace(0, 2*pi, 1000);
plot(cos(theta), sin(theta), '--', 'LineWidth', 1.5)
grid on
axis equal
xlabel('Real Part')
ylabel('Imaginary Part')
title('Pole-Zero Plot')
legend('Zeros','Poles','Unit Circle','Location','Best')

Nfft = 1024;
w = linspace(0, 2*pi, Nfft);
H = zeros(1, Nfft);
for i = 1:Nfft
    z = exp(1j*w(i));
    H(i) = polyval(num, z^(-1)) / polyval(den, z^(-1));
end

figure
subplot(2,1,1)
plot(w, 20*log10(abs(H)), 'LineWidth', 1)
grid on
xlabel('Frequency (rad/sample)')
ylabel('Magnitude (dB)')
title('Magnitude Response')

subplot(2,1,2)
plot(w, angle(H), 'LineWidth', 1)
grid on
xlabel('Frequency (rad/sample)')
ylabel('Phase (radians)')
title('Phase Response')
