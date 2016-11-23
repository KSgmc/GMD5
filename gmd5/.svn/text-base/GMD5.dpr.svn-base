program GMD5;

{$APPTYPE CONSOLE}

{$R *.res}

uses
  System.SysUtils,
  IdHashMessageDigest,
  System.Classes,
  IniFiles,
  TestFramework,
  TextTestRunner;

var
  bkp,  Codigo :String;
  IdMD5: TIdHashMessageDigest5;
  val : TFileStream;
  md5Ini, gravaIni : TiniFile;

begin
  val := nil;
  IdMD5 := nil;
try
    // Le o banco a ser codificado

    md5Ini := TIniFile.Create('C:\md5\script.ini');
    bkp := md5Ini.ReadString('ARQUIVO','ORIGEM','Erro no arquivo .ini');

    // Cria arquivo MD5
    IdMD5 := TIdHashMessageDigest5.Create;

    if not FileExists(bkp) then
    begin
      Writeln('Não foi possivel encontrar o caminho do arquivo .ini');
      Halt(1);
    end
    else
    begin
      val := TFileStream.Create(bkp, fmOpenRead or fmShareDenyWrite);
      Codigo :=IdMD5.HashStreamAsHex(val);
    end;

    // Grava arquivo ini
    gravaIni := TIniFile.Create('C:\md5\script.ini');
    gravaIni.WriteString('MD5','ORIGEM',Codigo);

  except

    Writeln('Não foi possivel executar MD5');
    Halt(1);

  end;
end.
