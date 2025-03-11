# Assignment 4: Getting Funcy

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%204%3A%20Getting%20Funcy/Assignment4.pdf)

## Solution
```matlab
% Assignment 4 (Talha Akhlaq) (3/11/2025) (ECE210-A) (Prof. Darius)

% Question 1:
dotproduct = @(x, y) x' * y; 

% Question 2:
function [orthonormal] = is_orthonormal(X)
    dotproduct = @(x, y) x' * y; 
        for i = 1:size(X, 2)
        if abs(norm(X(:, i)) - 1) > 1000 * eps
            orthonormal = false;
            return;
        end
        end
    for i = 1:size(X, 2)
        for j = i+1:size(X, 2)
            if abs(dotproduct(X(:, i), X(:, j))) > 1000 * eps
                orthonormal = false;
                return;
            end
        end
    end
    orthonormal = true;
end

% Question 3:
function [Y] = gram_schmidt(X)
    dotproduct = @(x, y) x' * y;     
    if is_orthonormal(X)
        Y = X;
        return;
    end    
    Y = zeros(size(X)); 
    for i = 1:size(X, 2)
        column = X(:, i);        
        for j = 1:i-1
            projection = dotproduct(Y(:, j), column) * Y(:, j);
            column = column - projection;
        end        
        Y(:, i) = column / norm(column);
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

