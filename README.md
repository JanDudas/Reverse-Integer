# Reverse-Integer

/**
 * @param {number} x
 * @return {number}
 */
var reverse = function (x) {

    let
        result = 0;
    x = parseInt(Number(x));

    let lowest = Math.pow(-2, 31), hghest = (Math.pow(2, 31) - 1);
    if ((x < lowest) || (x > hghest)) {
        return result;
    }
    let
        isNegative = false;
    if (x < 0) {
        isNegative = true;
        x = x * (-1);
    }

    let
        actualNumber = x, numbersArray = [], multiPlayer = 1;
    while (actualNumber > 0) {
        lastNumber = parseInt(actualNumber % 10);
        numbersArray.push(lastNumber);
        actualNumber = parseInt(actualNumber / 10);
    }

    let sizeOfField = numbersArray.length;
    for (var int = 0; int < sizeOfField - 1; int++) {
        multiPlayer = multiPlayer * 10;
    }

    for (var i = 0; i < sizeOfField; i++) {
        result += numbersArray[parseInt(i)] * multiPlayer;
        multiPlayer = multiPlayer / 10;
    }

    if (isNegative) {
        result = result * (-1);
    }
    if ((result < lowest) || (result > hghest)) {
        return 0;
    }
    return result;
};
