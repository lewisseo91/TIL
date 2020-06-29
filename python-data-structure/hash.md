# python

## hash

## hash & hash collision 방지 (충돌 방지)

#### 충돌방지 없는 hash table                    

    hashtable = list([0 for i in range(8)])

    def get_key(data):
        return hash(data)

    def hash_function(key):
        return key % 8 // 원하는 테이블 사이즈

    def save_data(data, value):
        hash_address = hash_function(get_key(data))
        hash_table[hash_address] = value

    def read_data(data, value):
        hash_address = hash_function(get_key(data))
        return hash_table[hash_address]

#### 충돌방지 hash table                    

    hashtable = list([0 for i in range(8)])

    def get_key(data):
        return hash(data)

    def hash_function(key):
        return key % 8 // 원하는 테이블 사이즈

    def save_data(data, value):
        index_key = get_key(data)
        hash_address = hash_function(index_key)
        if hash_table[hash_address] != 0: // 키가 있다.
            for index in range(len(hash_table[hash_address])) // 테이블 안에 추가 되어 있는거 불러서
                if hash_table[hash_address][index_key][0] == index_key: // 키가 들어 있다.
                    hash_table[hash_address][index_key][1] = value
                    return
            hash_table[hash_address].append([index_key, value]); // 키에 추가
        else : // 키가 없다.
            hash_table[hash_address] = [[index_key, value]]; // table에 추가

    def read_data(data, value):
        index_key = get_key(data)
        hash_address = hash_function(index_key)
        if hash_table[hash_address] != 0: // 키가 있다.
            for index in range(len(hash_table[hash_address])):
                if hash_table[hash_address][index][0] == index_key:
                    return hash_table[hash_address][index][1]
            return None; // 리스트를 다 돌았는데 내가 원하는 키의 밸류값이 없다.
        else : // 키가 없다.
            return None; // 리턴 할 거도 없다.