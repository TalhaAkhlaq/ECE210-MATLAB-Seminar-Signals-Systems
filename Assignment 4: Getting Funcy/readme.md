# Assignment 4: Getting Funcy

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%204%3A%20Getting%20Funcy/Assignment4.pdf)

## Solution
```matlab
% Assignment 4 (Talha Akhlaq) (3/11/2025) (ECE210-A) (Prof. Darius)

% Question 1:
dotfunction = @(x, y) x' * y; 

% Question 2:
function [is_orthonormal] = is_orthonormal(A)
    dotfunction = @(u, v) u' * v;
    for col = 1:size(A, 2)
        if abs(norm(A(:, col)) - 1) > 1000 * eps
            is_orthonormal = false;
            return;
        end
    end
    for col = 1:size(A, 2)
        for col2 = col+1:size(A, 2)
            if abs(dotfunction(A(:, col), A(:, col2))) > 1000 * eps
                is_orthonormal = false;
                return;
            end
        end
    end
    is_orthonormal = true;
end

% Question 3:
function Q = gram_schmidt(B)
    dotfunction = @(p, q) p' * q;
    if is_orthonormal(B)
        Q = B;
        return;
    end
    Q = zeros(size(B));
    for i = 1:size(B, 2)
        v = B(:, i);
        for j = 1:i-1
            v = v - dotfunction(Q(:, j), v) * Q(:, j);
        end
        Q(:, i) = v / norm(v);
    end
end

% Question 4:
M = randi(15, 4, 4) + 1j * randi(15, 4, 4);
disp('Original Matrix M:');
disp(M);
N = gram_schmidt(M);
disp('Orthonormalized Matrix N:');
disp(N);
result = is_orthonormal(N);
disp('Output:');
disp(result);


