import view.CadastroeditarMenuItemFrame; import java.io.; import java.util.;

public class CadastroAlunos { public class Controlador {

private Alunos alunosCadastroFrame;
private Aluno[] alunos;
private int pos;


public class CadastroAlunos {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<String> alunos = new ArrayList<>();
        List<Double> notas = new ArrayList<>();

        // Carregar nomes e notas salvos anteriormente, se houver
        carregarDados(alunos, notas);

        boolean executando = true;
        while (executando) {
            System.out.println("\nMenu:");
            System.out.println("1. Cadastrar aluno e nota");
            System.out.println("2. Listar alunos e notas");
            System.out.println("3. Editar nota de aluno");
            System.out.println("4. Calcular média dos alunos");
            System.out.println("5. Salvar e sair");

            int opcao = scanner.nextInt();
            scanner.nextLine(); // Consumir a quebra de linha após o próximoInt()

            switch (opcao) {
                case 1:
                    System.out.print("Digite o nome do aluno: ");
                    String nome = scanner.nextLine();
                    alunos.add(nome);
                    System.out.print("Digite a nota do aluno: ");
                    double nota = scanner.nextDouble();
                    notas.add(nota);
                    System.out.println("Aluno e nota cadastrados com sucesso!");
                    break;
                case 2:
                    if (alunos.isEmpty()) {
                        System.out.println("Nenhum aluno cadastrado.");
                    } else {
                        System.out.println("Lista de alunos e notas:");
                        for (int i = 0; i < alunos.size(); i++) {
                            System.out.println(alunos.get(i) + ": " + notas.get(i));
                        }
                    }
                    break;
                case 3:
                    if (alunos.isEmpty()) {
                        System.out.println("Nenhum aluno cadastrado para editar a nota.");
                    } else {
                        System.out.print("Digite o índice do aluno cuja nota deseja editar: ");
                        int indice = scanner.nextInt();
                        scanner.nextLine(); // Consumir a quebra de linha após o próximoInt()
                        if (indice >= 0 && indice < alunos.size()) {
                            System.out.print("Digite a nova nota para o aluno: ");
                            double novaNota = scanner.nextDouble();
                            notas.set(indice, novaNota);
                            System.out.println("Nota do aluno editada com sucesso!");
                        } else {
                            System.out.println("Índice inválido.");
                        }
                    }
                    break;
                case 4:
                    if (alunos.isEmpty()) {
                        System.out.println("Nenhum aluno cadastrado para calcular a média.");
                    } else {
                        double media = calcularMedia(notas);
                        System.out.println("A média dos alunos é: " + media);
                    }
                    break;
                case 5:
                    salvarDados(alunos, notas);
                    System.out.println("Dados salvos. Encerrando o programa.");
                    executando = false;
                    break;
                default:
                    System.out.println("Opção inválida. Por favor, escolha uma opção válida.");
            }
        }

        scanner.close();
    }

    private static void carregarDados(List<String> alunos, List<Double> notas) {
        try (BufferedReader reader = new BufferedReader(new FileReader("alunos_notas.txt"))) {
            String linha;
            while ((linha = reader.readLine()) != null) {
                String[] partes = linha.split(":");
                alunos.add(partes[0]);
                notas.add(Double.parseDouble(partes[1]));
            }
        } catch (IOException e) {
            System.out.println("Erro ao carregar dados dos alunos: " + e.getMessage());
        }
    }

    private static void salvarDados(List<String> alunos, List<Double> notas) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("alunos_notas.txt"))) {
            for (int i = 0; i < alunos.size(); i++) {
                writer.write(alunos.get(i) + ":" + notas.get(i));
                writer.newLine();
            }
        } catch (IOException e) {
            System.out.println("Erro ao salvar dados dos alunos: " + e.getMessage());
        }
    }

    private static double calcularMedia(List<Double> notas) {
        double soma = 0;
        for (double nota : notas) {
            soma += nota;
        }
        return notas.isEmpty() ? 0 : soma / notas.size();
    }
}
} }package model;

import javax.swing.JButton;

public class Aluno {

private String nome;
private double nota;


public String getnome() {
    return nome;
}

public void setnome(String nome) {
    this.nome = nome;
}

public double getnota() { 
    return nota;
}

public void setnota(nota nota) {
    this.nota = nota;
}

public String getString() {
    return String;
}
public void setString(String String) {
    this.nome = String;
}
} package view;

import javax.swing.*;
public class AlunoFrame {

private TextField nomeTextField;
private JButton okButton;
private JButton cancelarButton;
private TextField notaTextField;
private Controlador controlador;
private Aluno aluno;
private boolean editando;

public JButton getnomeTextField() {
    return nomeTextField;
}

public void setnomeTextField(JButton nomeTextField) {
    this.nomeTextField = nomeTextField;
}

public Aluno getAluno() {
    return aluno;
}

public void setAluno(Aluno aluno) {
    this.aluno = aluno;
}

public JButton getcancelarButton() {
    return cancelarButton;
}

public void setcancelarButton(JButton cancelarButton) {
    this.cancelarButton = cancelarButton;
}

public Controlador getControlador() {
    return controlador;
}

public void setControlador(Controlador controlador) {
    this.controlador = controlador;
}

public static void main(Controlador[] args) {

}

private void thisWindowClosing(){

}

private void cancelarButtonActionPerformed(){
    
}
private void okButtonActionPerformed(){
    
}
private void carregarDados(){
    return CadastroAlunoFrame;
}
} package view;

import java.util.List;
import javax.swing.*;

public class CadastroeditarMenuItemFrame {

private static final String CadastroeditarMenuItemFrame = null;
private JButton cadastrarMenuItem;
private editarMenuItem editarMenuItem;
private JList editarMenuItemsList;
private Controlador controlador;

public JMenuItem getcadastrarMenuItem() {
    return cadastrarMenuItem;
}

public void setcadastrarMenuItem(JButton cadastrarMenuItem) {
    this.cadastrarMenuItem = cadastrarMenuItem;
}

public editarMenuItem geteditarMenuItem() {
    return editarMenuItem;
}

public void seteditarMenuItem(editarMenuItem editarMenuItem) {
    this.editarMenuItem = editarMenuItem;
}

public JList geteditarMenuItemList() {
    return editarMenuItemsList;
}

public void seteditarMenuItemList() {
    this.editarMenuItemsList = editarMenuItemsList;
}

public Controlador getControlador() {
    return controlador;
}

public void setControlador(Controlador controlador) {
    this.controlador = controlador;
}

public static void main(Controlador[] args) {

}

private void thisWindowClosing(){

}

private void cadastrarMenuItemActionPerformed(){
    
}
private void editarMenuItemActionPerformed(){
    
}
private void carregarDados(){
    
    return CadastroeditarMenuItemFrame;
}

private void atualizarDados(){
editarMenuItem = new editarMenuItem(); 
}

}

package view;

import javax.swing.*;

public class TurmaFrame {

    private JButton listarAlunosButton;
    private JButton resultdosButton;
    private JButton novoAlunoButton;
    private Controlador controlador;

    public JButton getListarAlunosButton() {
        return listarAlunosButton;
    }

    public void setListarAlunosButton(JButton listarAlunosButton) {
        this.listarAlunosButton = listarAlunosButton;
    }

    public JButton getResultdosButton() {
        return resultdosButton;
    }

    public void setResultdosButton(JButton resultdosButton) {
        this.resultdosButton = resultdosButton;
    }

    public JButton getNovoAlunoButton() {
        return novoAlunoButton;
    }

    public void setNovoAlunoButton(JButton novoAlunoButton) {
        this.novoAlunoButton = novoAlunoButton;
    }

    public Controlador getControlador() {
        return controlador;
    }

    public void setControlador(Controlador controlador) {
        this.controlador = controlador;
    }

    public static void main(String[] args) {

    }

    private void thisWindowClosing(){

    }

    private void novoAlunoButtonActionPerformed(){
        
    }
}
