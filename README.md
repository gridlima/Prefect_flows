
from prefect import task
from prefect import flow
from prefect.schedules import IntervalSchedule

#Definindo tarefas--

@task
def extract_data():
    # Para extrair os dados
    return data

@task
def transform_data(data):
    # Para transformar os dados
    return transformed_data

@task
def load_data(transformed_data):
    # Para carregar os dados transformados

    pass

#Definindo um fluxo--

with Flow ("meu_fluxo") as flow:
    data = extract_data()
    transformed_data = transform_data(data)
    load_data(transformed_data)

#Executando o fluxo--

flow.run()

#Agendamento do fluxo--

schedule = IntervalSchedule(interval=timedelta(days=1))
flow.shedule = schedule


