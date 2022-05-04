db.companies.find({"name": "Babelgum"}, {_id: 0, "name": 1});

db.companies.find({"number_of_employees": {$gt: 5000}}).sort({"number_of_employees": 1}).limit(20).pretty();

db.companies.find({"founded_year": {$gte: 2000, $lte: 2005}}, {_id: 0, "name": 1, "founded_year": 1});

db.companies.find({"ipo.valuation_amount": {$gt: 100000000}, "founded_year": {$lt: 2010}}, {"name": 1, "ipo": 1, _id: 0});

db.companies.find({"number_of_employees": {$lt: 1000}, "founded_year": {$lt: 2005}}).sort({"number_of_employees": 1}).limit(10);

db.companies.find({"partners": {$exists: false}}).pretty();

db.companies.find({"category_code": {$type: "null"}}).pretty();

db.companies.find({"number_of_employees": {$gte: 100, $lt: 1000}}, {_id: 0, "name": 1, "number_of_employees": 1}).pretty();

db.companies.find().sort({"ipo.valuation_amount": -1}).pretty();

db.companies.find().sort({"number_of_employees": -1}).limit(10).pretty();

db.companies.find({"founded_month": {$gt: 6}}).limit(1000).pretty();

db.companies.find({"founded_year": {$lt: 2000}, "acquisition.price_amount": {$gt: 10000000}}).pretty();

db.companies.find({"acquisition.acquired_year": {$gt: 2010}}, {"name": 1, "acquisition": 1, _id: 0}).sort({"acquisition.price_amount": 1}).pretty();

db.companies.find({}, {"name": 1, "founded_year": 1, _id: 0}).sort({"founded_year": 1}).pretty();

db.companies.find({"founded_day": {$lte: 7, $not: {$type: "null"}}}).sort({"acquisition.price_amount": -1}).limit(10).pretty();

db.companies.find({"category_code": "web", "number_of_employees": {$gt: 4000}}).sort({"number_of_employees": 1}).pretty();

db.companies.find({$and: [{"acquisition.price_amount": {$gt: 10000000}}, {"acquisition.price_currency_code": "EUR"}]}).pretty();

db.companies.find({"acquisition.acquired_month": {$lte: 3}}, {"name": 1, "acquisition": 1, _id: 0}).limit(10).pretty();

db.companies.count({"founded_year": {$gte: 2000, $lte: 2010}, $or: [{"acquisition.acquired_year": {$gt: 2011}}, {"acquisition": null}, {"acquisition.acquired_year": null}]});
