<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerenciador de Notas de Boletim</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #f2f2f2;
        }
        .button {
            margin: 5px;
        }
        .hidden {
            display: none;
        }
        @media print {
            body {
                margin: 0;
            }
            table {
                page-break-inside: auto;
            }
            tr {
                page-break-inside: avoid; 
                page-break-after: auto; 
            }
        }
    </style>
</head>
<body>

<div id="loginContainer">
    <h2>Login</h2>
    <input type="text" id="username" placeholder="Usuário">
    <input type="password" id="password" placeholder="Senha">
    <button class="button" onclick="login()">Entrar</button>
    <p id="loginError" style="color: red;"></p>
</div>

<div id="appContainer" class="hidden">
    <h1>Gerenciador de Notas de Boletim</h1>
    
    <button class="button" onclick="logout()">Deslogar</button>

    <h2>Adicionar Aluno</h2>
    <input type="text" id="studentName" placeholder="Nome do Aluno">
    <select id="course">
        <option value="">Selecione o Curso</option>
        <option value="Médio Técnico">Médio Técnico</option>
        <option value="Formação Profissional">Formação Profissional</option>
    </select>
    <select id="class">
        <option value="">Selecione a Turma</option>
        <option value="A">A</option>
        <option value="B">B</option>
        <option value="C">C</option>
        <option value="D">D</option>
    </select>
    <button class="button" onclick="addStudent()">Adicionar Aluno</button>

    <h3>Adicionar Disciplina ao Aluno</h3>
    <select id="studentSelect"></select>

    <select id="disciplineSelect">
        <option value="">Selecione a Disciplina</option>
        <option value="Redação">Redação</option>
        <option value="Gramática">Gramática</option>
        <option value="Educação Física">Educação Física</option>
        <option value="Literatura">Literatura</option>
        <option value="Geografia">Geografia</option>
        <option value="Inglês">Inglês</option>
        <option value="História">História</option>
        <option value="Projeto de Vida">Projeto de Vida</option>
        <option value="Artes">Artes</option>
        <option value="Matemática">Matemática</option>
        <option value="Filosofia">Filosofia</option>
        <option value="Física">Física</option>
        <option value="Química">Química</option>
        <option value="Biologia">Biologia</option>
        <option value="Formação Profissional">Formação Profissional</option>
        <option value="Inovaê">Inovaê</option>
    </select>

    <select id="unit">
        <option value="">Selecione a Unidade</option>
        <option value="1">Unidade 1</option>
        <option value="2">Unidade 2</option>
        <option value="3">Unidade 3</option>
        <option value="4">Unidade 4</option>
    </select>
    <select id="evaluation1">
        <option value="">Avaliação 1</option>
        <option value="A">A</option>
        <option value="PA">PA</option>
        <option value="ND">ND</option>
    </select>
    <select id="evaluation2">
        <option value="">Avaliação 2</option>
        <option value="A">A</option>
        <option value="PA">PA</option>
        <option value="ND">ND</option>
    </select>
    <select id="finalGrade">
        <option value="">Menção Final</option>
        <option value="D">Desenvolveu (D)</option>
        <option value="ND">Não Desenvolveu (ND)</option>
    </select>
    <button class="button" onclick="addDiscipline()">Adicionar Disciplina</button>

    <h2>Consultar Alunos</h2>
    <input type="text" id="searchName" placeholder="Pesquisar Aluno">
    <button class="button" onclick="searchStudent()">Pesquisar</button>

    <h3>Imprimir Boletim</h3>
    <div>
        <label>Selecione as Unidades:</label>
        <div>
            <label><input type="checkbox" class="unitCheckbox" value="1"> Unidade 1</label>
            <label><input type="checkbox" class="unitCheckbox" value="2"> Unidade 2</label>
            <label><input type="checkbox" class="unitCheckbox" value="3"> Unidade 3</label>
            <label><input type="checkbox" class="unitCheckbox" value="4"> Unidade 4</label>
        </div>
    </div>
    <div>
        <label><input type="radio" name="reportType" value="full" checked> Incluir Avaliações</label>
        <label><input type="radio" name="reportType" value="summary"> Somente Menção e Situação</label>
    </div>
    <button class="button" onclick="printAllReports()">Imprimir Todos os Boletins</button>

    <table id="studentTable">
        <thead>
            <tr>
                <th>Nome</th>
                <th>Curso</th>
                <th>Turma</th>
                <th>Disciplina</th>
                <th>Unidade</th>
                <th>Avaliação 1</th>
                <th>Avaliação 2</th>
                <th>Menção Final</th>
                <th>Situação</th>
                <th>Ações</th>
            </tr>
        </thead>
        <tbody>
            <!-- Alunos e disciplinas serão adicionados aqui -->
        </tbody>
    </table>
</div>

<script>
    const students = [];
    let userRole = '';

    function login() {
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;

        if (username === 'professor' && password === 'professor') {
            userRole = 'professor';
            document.getElementById('loginContainer').classList.add('hidden');
            document.getElementById('appContainer').classList.remove('hidden');
            alert('Bem-vindo, Professor!');
            hideAdminFeatures();
        } else if (username === 'administrador' && password === 'admsenac2024') {
            userRole = 'admin';
            document.getElementById('loginContainer').classList.add('hidden');
            document.getElementById('appContainer').classList.remove('hidden');
            alert('Bem-vindo, Administrador!');
        } else {
            document.getElementById('loginError').textContent = 'Usuário ou senha incorretos.';
        }
    }

    function hideAdminFeatures() {
        document.getElementById('studentName').disabled = true;
        document.getElementById('course').disabled = true;
        document.getElementById('class').disabled = true;
        document.getElementById('studentSelect').disabled = true;
        document.getElementById('disciplineSelect').disabled = true;
        document.getElementById('unit').disabled = true;
        document.getElementById('evaluation1').disabled = true;
        document.getElementById('evaluation2').disabled = true;
        document.getElementById('finalGrade').disabled = true;
    }

    function logout() {
        userRole = '';
        document.getElementById('loginContainer').classList.remove('hidden');
        document.getElementById('appContainer').classList.add('hidden');
        alert('Você deslogou com sucesso.');
    }

    function addStudent() {
        if (userRole !== 'admin') {
            alert('Acesso negado. Apenas administradores podem adicionar alunos.');
            return;
        }

        const name = document.getElementById('studentName').value;
        const course = document.getElementById('course').value;
        const classValue = document.getElementById('class').value;

        if (name && course && classValue) {
            const student = {
                name,
                course,
                classValue,
                disciplines: []
            };

            students.push(student);
            updateStudentSelect();
            updateStudentTable();
            alert(`Aluno ${name} adicionado com sucesso!`);
            clearInputs();
        } else {
            alert('Por favor, preencha todos os campos.');
        }
    }

    function updateStudentSelect() {
        const select = document.getElementById('studentSelect');
        select.innerHTML = '';
        students.forEach((student, index) => {
            const option = document.createElement('option');
            option.value = index;
            option.textContent = student.name;
            select.appendChild(option);
        });
    }

    function addDiscipline() {
        const studentIndex = document.getElementById('studentSelect').value;
        const disciplineName = document.getElementById('disciplineSelect').value;
        const unit = document.getElementById('unit').value;
        const evaluation1 = document.getElementById('evaluation1').value;
        const evaluation2 = document.getElementById('evaluation2').value;
        const finalGrade = document.getElementById('finalGrade').value;

        if (studentIndex !== '' && disciplineName && unit && finalGrade) {
            const student = students[studentIndex];
            const discipline = {
                discipline: disciplineName,
                unit,
                evaluation1,
                evaluation2,
                finalGrade,
                situation: finalGrade === 'D' ? 'Aprovado' : 'Reprovado'
            };

            student.disciplines.push(discipline);
            updateStudentTable();
            alert(`Disciplina ${disciplineName} adicionada ao aluno ${student.name}.`);
            clearDisciplineInputs();
        } else {
            alert('Por favor, preencha todos os campos.');
        }
    }

    function updateStudentTable() {
        const tbody = document.getElementById('studentTable').querySelector('tbody');
        tbody.innerHTML = '';
        students.forEach(student => {
            student.disciplines.forEach(discipline => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${student.name}</td>
                    <td>${student.course}</td>
                    <td>${student.classValue}</td>
                    <td>${discipline.discipline}</td>
                    <td>${discipline.unit}</td>
                    <td>${discipline.evaluation1}</td>
                    <td>${discipline.evaluation2}</td>
                    <td>${discipline.finalGrade}</td>
                    <td>${discipline.situation}</td>
                    <td><button class="button" onclick="removeDiscipline('${student.name}', '${discipline.discipline}')">Remover</button></td>
                `;
                tbody.appendChild(row);
            });
        });
    }

    function clearInputs() {
        document.getElementById('studentName').value = '';
        document.getElementById('course').value = '';
        document.getElementById('class').value = '';
    }

    function clearDisciplineInputs() {
        document.getElementById('disciplineSelect').value = '';
        document.getElementById('unit').value = '';
        document.getElementById('evaluation1').value = '';
        document.getElementById('evaluation2').value = '';
        document.getElementById('finalGrade').value = '';
    }

    function searchStudent() {
        const searchName = document.getElementById('searchName').value.toLowerCase();
        const filteredStudents = students.filter(student => student.name.toLowerCase().includes(searchName));
        
        const tbody = document.getElementById('studentTable').querySelector('tbody');
        tbody.innerHTML = '';
        filteredStudents.forEach(student => {
            student.disciplines.forEach(discipline => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${student.name}</td>
                    <td>${student.course}</td>
                    <td>${student.classValue}</td>
                    <td>${discipline.discipline}</td>
                    <td>${discipline.unit}</td>
                    <td>${discipline.evaluation1}</td>
                    <td>${discipline.evaluation2}</td>
                    <td>${discipline.finalGrade}</td>
                    <td>${discipline.situation}</td>
                    <td><button class="button" onclick="removeDiscipline('${student.name}', '${discipline.discipline}')">Remover</button></td>
                `;
                tbody.appendChild(row);
            });
        });
    }

    function removeDiscipline(studentName, disciplineName) {
        const student = students.find(s => s.name === studentName);
        student.disciplines = student.disciplines.filter(d => d.discipline !== disciplineName);
        updateStudentTable();
        alert(`Disciplina ${disciplineName} removida do aluno ${studentName}.`);
    }

    function printAllReports() {
        const selectedUnits = Array.from(document.querySelectorAll('.unitCheckbox:checked')).map(checkbox => checkbox.value);
        const reportType = document.querySelector('input[name="reportType"]:checked').value;

        let reportContent = '<html><head><title>Relatório de Notas</title></head><body>';
        reportContent += '<h1>Instituição SENAC</h1>';
        reportContent += '<h2>Relatório de Notas</h2>';
        reportContent += '<button class="button" onclick="window.print()">Imprimir</button>'; // Botão de imprimir

        students.forEach(student => {
            reportContent += `<h3>Boletim de ${student.name}</h3>`;
            reportContent += `<p>Curso: ${student.course}</p>`;
            reportContent += `<p>Turma: ${student.classValue}</p>`;

            selectedUnits.forEach(unit => {
                reportContent += `<h4>Unidade ${unit}</h4>`;
                reportContent += '<table>';
                reportContent += `
                    <thead>
                        <tr>
                            <th>Disciplina</th>
                            ${reportType === 'full' ? '<th>Avaliação 1</th><th>Avaliação 2</th>' : ''}
                            <th>Menção Final</th>
                            <th>Situação</th>
                        </tr>
                    </thead>
                    <tbody>`;

                student.disciplines.forEach(discipline => {
                    if (discipline.unit === unit) {
                        reportContent += `
                            <tr>
                                <td>${discipline.discipline}</td>
                                ${reportType === 'full' ? `<td>${discipline.evaluation1}</td><td>${discipline.evaluation2}</td>` : ''}
                                <td>${discipline.finalGrade}</td>
                                <td>${discipline.situation}</td>
                            </tr>`;
                    }
                });

                reportContent += '</tbody></table><hr>';
            });
        });

        reportContent += '</body></html>';
        
        const reportWindow = window.open('', 'Relatório', 'width=800,height=600');
        reportWindow.document.write(reportContent);
        reportWindow.document.close();

        reportWindow.onload = function() {
            reportWindow.print();
        };
    }
</script>

</body>
</html>
