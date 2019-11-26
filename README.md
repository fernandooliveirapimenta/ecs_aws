# O que é ECS
Serviço regional em várias zonas de disponibilidade em uma região.

Serviço gerenciado altamente escalável, com alta performance na orquestracao
de containers docker
- Autoscaling
- Load balancing
- IMA
- Networking
- Logging
- Monitoring


AWS Fargate elimina a necessidade de interagir com servidores ou ter dor de cabeça
no gerenciamento e escolha do hardware necessário.

#Arquitetura

- Primeiro devo construir uma imagem do meu container
 Docker file
- Armazenar ela em um registry ECR ou docker hub

- Para rodar no ECS precisamos de 
- taskdefintion:
	arquivo json que define um ou mais containers que formaram
	a aplicação, portas, volumes e etc.
	no máximo 10 containers por taskdefinition.
- Tarefas e programação (tasks and scheduling)
	instanciação de uma taskdefinition dentro de um clusteer
	vc pode especificar o nũmero de tarefas que serão executadas
- Clusters
	agrupamento lógico de recursos Fargate Totalmente gerenciado ou EC2 
	gerenciado pelo usuario.
	cada instancia tera um agent do ECS instalado.
	o ECS fara download das imagens apartir de um registro



#ECS cli
sudo curl -so /usr/local/bin/ecs-cli https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-latest
sudo chmod +x /usr/local/bin/ecs-cli

sudo yum -y install jq gettext

#AWS cli
export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r .region)
echo "export AWS_REGION=${AWS_REGION}" >> ~/.bash_profile
aws configure set default.region ${AWS_REGION}
aws configure get default.region

