class ParkingLot:
    def __init__(self, capacity):
        self.capacity = capacity
        self.available_slots = capacity
        self.occupied_slots = {}  # Slot number: Vehicle ID

    def park_vehicle(self, vehicle_id):
        if self.available_slots > 0:
            slot_number = self.find_available_slot()
            self.occupied_slots[slot_number] = vehicle_id
            self.available_slots -= 1
            print(f"Vehicle {vehicle_id} parked in slot {slot_number}")
            return slot_number
        else:
            print("Parking lot is full.")
            return None

    def find_available_slot(self):
        for i in range(1, self.capacity + 1):
            if i not in self.occupied_slots:
                return i
        return None

    def vacate_slot(self, slot_number):
        if slot_number in self.occupied_slots:
            del self.occupied_slots[slot_number]
            self.available_slots += 1
            print(f"Slot {slot_number} vacated.")
        else:
            print(f"Slot {slot_number} is already empty.")

    def get_available_slots(self):
        return self.available_slots

    def get_occupied_slots(self):
        return self.occupied_slots

# Example Usage
parking_lot = ParkingLot(10)

parking_lot.park_vehicle("Car1")
parking_lot.park_vehicle("Car2")
parking_lot.vacate_slot(1)
print(f"Available Slots: {parking_lot.get_available_slots()}")
print(f"Occupied Slots: {parking_lot.get_occupied_slots()}")

