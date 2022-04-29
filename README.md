# dz2904
class HotelNew:
    def __init__(self, num_sgl = 5, num_dbl = 5, num_jsuite = 3, num_suite = 1 ):
        self._rooms = {"SGL":{"num":num_sgl, "free":num_sgl, "price": 1000} ,"DBL" :{"num":num_dbl, "free":num_dbl, "price": 3000} ,"Junior Suite":{"num": num_jsuite, "free":num_jsuite, "price": 7000} ,"Suite":{"num":num_suite, "free": num_suite, "price": 15000} } # информация о статусе номеров
    
    # метод для бронирования номера по уникальному значению в списке
    def occypy(self, room_type):
        if self._rooms[room_type]["free"] > 0:
            self._rooms[room_type]["free"] -= 1  # бронируем номер
        else:
            raise RuntimeError(f"Нет свободных номеров типа {room_type} ")
 
    def free(self, room_type):
        if self._rooms[room_type]["num"]> self._rooms[room_type]["free"]:
            self._rooms[room_type]["free"] += 1 # освобождаем номер
        else:
            raise RuntimeError("Всё номера уже свободны")

    def __str__(self):
        a = ''
        for key in self._rooms:
            a += "Номера вида" + key + " сейчас доступны в количестве" + str(self._rooms[key]["num"]) + ". Стоимость номера" +str(self._rooms[key]["price"])+"у.е.\n" 
        return a

hotel = HotelNew() 

print(hotel._rooms) 

hotel.occypy("SGL" )

print(hotel._rooms)

hotel.free("SGL" )

print(hotel._rooms)
