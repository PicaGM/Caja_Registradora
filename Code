function checkCashRegister(price, cash, cid) {
  const unidadMonetaria = {
    "PENNY": 0.01,
    "NICKEL": 0.05,
    "DIME": 0.1,
    "QUARTER": 0.25,
    "ONE": 1,
    "FIVE": 5,
    "TEN": 10,
    "TWENTY": 20,
    "ONE HUNDRED": 100
  };

  let cambio = cash - price;
  let cambioDisponible = 0;

  for (let i = 0; i < cid.length; i++) {
    cambioDisponible += cid[i][1];
  }

  cambioDisponible = parseFloat(cambioDisponible.toFixed(2));

  if (cambio > cambioDisponible) {
    return { status: "INSUFFICIENT_FUNDS", change: [] };
  }

  if (cambio === cambioDisponible) {
    return { status: "CLOSED", change: cid };
  }

  let cambioEntregar = [];

  for (let i = cid.length - 1; i >= 0; i--) {
    const [nombreMoneda, valorMoneda] = cid[i];
    const valorMonedaUnidad = unidadMonetaria[nombreMoneda];
    let cantidadMoneda = (valorMoneda / valorMonedaUnidad).toFixed(0);
    let cantidadMonedasEntregar = 0;

    while (cambio >= valorMonedaUnidad && cantidadMoneda > 0) {
      cambio -= valorMonedaUnidad;
      cambio = parseFloat(cambio.toFixed(2));
      cantidadMonedasEntregar++;
      cantidadMoneda--;
    }

    if (cantidadMonedasEntregar > 0) {
      cambioEntregar.push([nombreMoneda, cantidadMonedasEntregar * valorMonedaUnidad]);
    }
  }

  if (cambio > 0) {
    return { status: "INSUFFICIENT_FUNDS", change: [] };
  }

  return { status: "OPEN", change: cambioEntregar };
}

checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
