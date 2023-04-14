% CORRECT RECONSTRUCTION COUNTS

function countsCorrectReconstructions

runs = 0;
correctRecons = 0;
verticesmin0 = [];

for i = linspace(1, 25, 25)
    [countsdum, verticesmin0dumm] = comparisonLoop;
    correctRecons = correctRecons + countsdum;
    verticesmin0 = [verticesmin0, verticesmin0dumm];
    runs = runs + 1;
    close all
end

runs
correctRecons
verticesmin_mean = mean(verticesmin0)

end
