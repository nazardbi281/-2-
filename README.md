class FileSystem:
    def __init__(self):
        self.structure = {}
    
    def create_file(self, path):
        # Логика создания файла
        pass
    
    def create_directory(self, path):
        # Логика создания каталога
        Pass
def delete_file(self, path):
    if path in self.structure:
        del self.structure[path]
    else:
        raise FileNotFoundError("Файл не найден")
def read_file(self, path, offset=0, length=4096):
    if path not in self.structure:
        raise FileNotFoundError("Файл не найден")
    return self.structure[path]['data'][offset:offset + length]
def write_file(self, path, data, offset=0):
    if path not in self.structure:
        self.create_file(path)  # Создание файла, если его нет
    existing_data = self.structure[path]['data']
    self.structure[path]['data'] = existing_data[:offset] + data + existing_data[offset + len(data):]
def check_access(self, path, mode):
    permissions = self.structure[path]['permissions']
    if mode not in permissions:
        raise PermissionError("Нет прав доступа")
from threading import Lock

class ThreadSafeFileSystem(FileSystem):
    def __init__(self):
        super().__init__()
        self.lock = Lock()
    
    def safe_write_file(self, path, data, offset):
        with self.lock:
            self.write_file(path, data, offset)
