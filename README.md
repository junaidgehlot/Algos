# Algos

const fibonacci = (n) => {
  const fib = [0, 1];
  for(let i = 2; i < n; i++){
    fib[i] = fib[i - 1] + fib[i - 2];
  }
  return fib;
}

const factorial = (n) => {
  let result = 1
  for(let i = 2; i <= n; i++){
      result = result * i;
  }
  return result;
}

const isPrime = (n) => {
  if(n < 2) return false;
  for(let i = 2; i < 5; i++){
    if(n % i === 0) return false
  }
  return true
}

const isPowerOfTwo = (n) => {
  while(n){
    if(n > 1 && n % 2 !== 0){
      return false;
    }
    n = n/2;
  }
  return true;
}

const binaryRecursive = (
  arr, 
  target, 
  firstIndex = 0, 
  lastIndex = arr.length - 1
  ) => {
  if(firstIndex >= lastIndex){
    return -1;
  }
  let middleIndex = Math.floor((firstIndex + lastIndex)/2);
  if(arr[middleIndex] === target){
    return middleIndex;
  }

  if(target > arr[middleIndex]){
    return binaryRecursive(arr, target, middleIndex + 1, lastIndex);
  }else{
    return binaryRecursive(arr, target, firstIndex, middleIndex - 1);
  }
}

const binarySearch = (arr, target, isRecursive = false) => {
  if(isRecursive){
    return binaryRecursive(arr, target)
  } else{    
  let firstIndex = 0
  let lastIndex = arr.length - 1;
  while(firstIndex <= lastIndex){
    let middleIndex  = Math.floor((firstIndex + lastIndex) / 2);
    if(arr[middleIndex] == target){
      return middleIndex;
    } 
    if(arr[middleIndex] < target){
        firstIndex = middleIndex + 1;      
    } else {
        lastIndex = middleIndex - 1;  
    }
  }
  return -1;
  }
}

const bubbleSort =  (arr) => {
  let isElementSwapped;
  do{
    isElementSwapped = false;    
     for(let i = 1; i < arr.length; i++){
      if(arr[i - 1] > arr[i]){
          const firstElement = arr[i - 1];
          arr[i - 1] =  arr[i];
          arr[i] = firstElement; 
          isElementSwapped = true;
        }  
      }
  }while(isElementSwapped);
  return arr;
}


const insertionSort = (arr, optimized = false) => {
if(!optimized){    
  let sortedArrayEnd = 0;
  while (sortedArrayEnd < arr.length - 1) {
    let numberToInsert = arr[sortedArrayEnd + 1];
    let counter = sortedArrayEnd;
    while(counter > -1) {
      let sortedArrItem = arr[counter];
      if(sortedArrItem > numberToInsert){
        arr[counter + 1] = sortedArrItem;
      }else{
        arr[counter + 1] = numberToInsert;
        break;
      }
      counter--;
    }
      sortedArrayEnd++   
    }
  return arr;
  }else{
    for(i = 1; i < arr.length; i++){
        let numberToInsert = arr[i];
        let j = i - 1;
        while(j >= 0 && arr[j] > numberToInsert){
          arr[j + 1] = arr[j];
          j--;
        }
      arr[j + 1] = numberToInsert;
    }
   return arr;
  }
}

const quickSort = (arr) => {
  if(arr && arr.length <= 0){
      return arr;
  }
  const arrLt = []; 
  const arrGt = [];
  const pivot = arr[arr.length - 1];
  for(let i = 0; i < arr.length - 1; i++){
      if(arr[i] > pivot){
        arrGt.push(arr[i]); 
      }else{
        arrLt.push(arr[i]);
      }
  }
  return [...quickSort(arrLt),pivot, ...quickSort(arrGt)];
}

const merge = (leftArr, rightArr) => {
  const sortedArr = [];
  while(leftArr.length && rightArr.length){
    if(leftArr[0] <= rightArr[0]){      
      sortedArr.push(leftArr.shift());
    }else{
      sortedArr.push(rightArr.shift());
    }
  }

  return [...sortedArr, ...leftArr, ...rightArr];
  
}


const mergeSort = (arr) => {
  if(arr && arr.length <= 1){
    return arr;
  }
  const mid = Math.floor(arr.length/2);
  const leftArr = arr.slice(0, mid);
  const rightArr = arr.slice(mid);  
  return merge(mergeSort(leftArr), mergeSort(rightArr))
}

const cartesianProduct = (arrOne, ArrTwo) => {
  let result = [];
  for (let i = 0; i < arrOne.length; i++) {
    for (let j = 0; j < ArrTwo.length; j++) {
      result.push([arrOne[i], ArrTwo[j]])
    }
  }
  return result;
}

const climbingStais = (n) => {
  if(n <= 2){
      return n;
  }

  return climbingStais(n - 2) +  climbingStais(n - 1)
}


const users = [{
  firstName: 'Saqlain',
  lastName: 'Gehlot',
  age:  11
},{
  firstName: 'Saif',
  lastName: 'Gehlot',
  age: 14
},
  {
  firstName: 'Junaid',
  lastName: 'Gehlot',
  age: 25
},
{
  firstName: 'Faisal',
  lastName: 'Gehlot',
  age: 28
}];

console.log(users.reduce((acc, curr) => {
 if(curr.age < 26){
   acc.push(curr.firstName)
 } 
return acc;
}, []))








