from pydantic import BaseModel

class AtletaBase(BaseModel):
    nome: str
    centro_treinamento: str
    categoria: str

class AtletaCreate(AtletaBase):
    cpf: str

class Atleta(AtletaBase):
    id: int
    cpf: str

    class Config:
        orm_mode = True
