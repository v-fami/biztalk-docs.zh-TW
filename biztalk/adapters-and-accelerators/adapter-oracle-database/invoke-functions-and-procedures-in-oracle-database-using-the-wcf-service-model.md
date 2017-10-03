---
title: "叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke functions and procedures using the WCF service model
- WCF service model, invoking functions and procedures
ms.assetid: 806fc803-3640-42d6-bdf9-53b08f9c7c50
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a6256491100939937113ac6f140adc031da0941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model"></a>叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現程序、 函數和封裝做為作業。 WCF 服務模型中的 WCF 用戶端上的方法以表示這些作業。 WCF 服務模型和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   **支援函式**。 Oracle 函式的傳回值會呈現為 WCF 用戶端方法的傳回值。 Oracle 參數被當成 WCF 用戶端方法 （具有適當的方向為定義以下） 的參數。  
  
-   **支援的程序**。 OUT 參數的 Oracle 程序的第一個會呈現為 WCF 用戶端方法的傳回值。 所有其他的 Oracle 參數當成 （具有適當的方向為定義以下） 的參數至 WCF 用戶端方法。  
  
-   **支援 Oracle 封裝**。 作業的名稱和其參數類型的命名空間會限定封裝名稱。  
  
-   **支援多載函式和程序**。  
  
-   **支援 IN、 OUT 和 IN，OUT 參數的程序和函式的基本 Oracle 資料型別**。 OUT 參數當成**出**WCF 用戶端方法的參數，並在 OUT 參數當成**ref**參數。  
  
-   **支援 IN、 OUT、 和 IN 出程序和函式，以及函式傳回值的 REF CURSOR 參數**。 如需詳細資訊，請參閱[執行作業使用 REF 資料指標在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)。  
  
-   **支援，OUT、 出記錄中的型別參數的程序和函式，以及函式傳回值**。 如需詳細資訊，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 這個主題使用 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT 中的範例中，多載程序。 此程序讀取記錄從 SCOTT/帳戶資料表為基礎的帳戶識別碼或帳戶名稱。 指令碼來產生這個程序和資料表所提供的 SDK 範例。 如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 下表顯示 WCF 用戶端和程序，為產生的方法名稱函式，以及封裝[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面。 多載函式或程序，除非單一 WCF 用戶端用來叫用的所有結構描述時，所有的結構描述中的程序或所有函式中的函式和封裝中的程序。  
  
|Oracle 成品|WCF 用戶端作業名稱|範例|  
|---------------------|-------------------------------|-------------|  
|程序|[結構描述]ProcedureClient。[PROC_NAME]|SCOTTProcedureClient.MYPROC|  
|函數|[結構描述]FunctionClient。[FUNC_NAME]|SCOTTProcedureClient.MYFUNC|  
|封裝 （程序或函數）|[結構描述]封裝 [PACKAGE_NAME] 用戶端。[PROC_NAME 或 FUNC_NAME]|SCOTTPackageMYPACKAGEClient.MYPROC|  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。  
  
 [FUNC_NAME] = Oracle 函式; 的名稱例如，MYFUNC。  
  
 [PACKAGE_NAME] = Oracle 封裝的名稱。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示 Oracle 記錄型別參數和傳回值，以及傳回 REF CURSOR 參數為複雜的 XML 型別包含 Oracle 記錄的資料列資料 （或欄位） 的結果集。 在 WCF 服務模型中，每個 XML 類型被以.NET 類別。此類別的屬性代表 REF 資料指標結果集的記錄類型的欄位。 Oracle 記錄類型永遠會表示為強型別.NET 類別。 但是，REF 資料指標結果集，可以表示為根據 REF CURSOR 本身是否宣告為強型別或弱型別是強型別或弱式型別的記錄。 表示 REF CURSOR 或記錄類型參數 （或傳回值） 會在基礎程序、 函數或封裝的唯一命名空間中產生類別。 下表顯示這些命名空間。  
  
|Oracle 成品|命名空間|範例|  
|---------------------|---------------|-------------|  
|程序|[BASE_NS]。 [結構描述]。程序。[PROC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT。Procedure.MYPROC|  
|函數|[BASE_NS]。 [結構描述]。函式。[FUNC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT。Function.MYFUNC|  
|封裝 （程序）|[BASE_NS]。 [結構描述]。封裝。[PACKAGE_NAME]。[PROC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYPROC|  
|封裝 （函式）|[BASE_NS]。 [結構描述]。封裝。[PACKAGE_NAME]。[FUNC_NAME]|microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYFUNC|  
|一般記錄集 （弱型別）|[BASE_NS]|microsoft.lobservices.oracledb._2007._03|  
  
 [BASE_NS] = 的基底配接器命名空間中。microsoft.lobservices.oracledb._2007._03。  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。  
  
 [FUNC_NAME] = Oracle 函式; 的名稱例如 MYFUNC。  
  
 [PACKAGE_NAME] = Oracle 封裝的名稱。  
  
 如需這些命名空間中如何使用記錄的參數資訊，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。 如需這些命名空間中如何使用 REF CURSOR 參數的資訊，請參閱[執行作業使用 REF 資料指標在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)。  
  
 一般情況下，Oracle 參數和傳回值會對應，如下所示的 WCF 用戶端方法中：  
  
-   Oracle IN 參數會對應至.NET （輸入） 的參數。  
  
-   Oracle OUT 參數會對應至.NET**出**參數。  
  
-   Oracle IN OUT 參數會對應至.NET **ref**參數。  
  
-   函式傳回值會對應到方法的傳回值。  
  
 不過，有兩個重要的例外狀況：  
  
-   REF CURSOR oracle IN OUT 參數會分割輸入的字串和輸出 (**出**) 記錄集。 這是因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示在 REF CUSROR 參數做為字串和 OUT REF CURSOR 參數為複雜類型 （資料錄集），無法合併至單一參數。  
  
-   OUT 參數的 Oracle 程序中的第一個會對應至 WCF 用戶端方法的傳回值。 這是標準的 WCF 行為。  
  
 下列範例會示範簡單 （載入 SCOTT 結構描述中） 的 Oracle 程序的一部分，會叫用它來產生 WCF 用戶端方法的簽章。 Oracle 程序有三個 IN 參數、 三個 IN OUT 參數，以及三個 OUT 參數。不過，WCF 用戶端方法未對應的 OUT 參數的第一個參數。 而是它會對應到方法的傳回值。  
  
```  
CREATE or REPLACE PROCEDURE Sample_Procedure   
    (  
     INNUMBER      IN         NUMBER,  
     INVARCHAR     IN         VARCHAR2,  
     INDATE        IN         DATE,  
     INOUTNUMBER   IN OUT     NUMBER,  
     INOUTVARCHAR  IN OUT     VARCHAR,  
     INOUTDATE     IN OUT     DATE,  
     OUTNUMBER     OUT        NUMBER,  
     OUTVARCHAR    OUT        VARCHAR2,  
     OUTDATE       OUT        DATE  
    ) AS   
    BEGIN  
  
        ...  
  
    END;  
    /  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTProcedureClient : System.ServiceModel.ClientBase<SCOTTProcedure>, SCOTTProcedure {  
  
    public System.Nullable<decimal> SAMPLE_PROCEDURE  
       (  
        System.Nullable<decimal> INNUMBER,   
        string INVARCHAR,   
        System.Nullable\<System.DateTime> INDATE,   
        ref System.Nullable<decimal> INOUTNUMBER,   
        ref string INOUTVARCHAR,   
        ref System.Nullable\<System.DateTime> INOUTDATE,   
        out string OUTVARCHAR,   
        out System.Nullable\<System.DateTime> OUTDATE  
        );  
}  
```  
  
### <a name="support-for-overloaded-procedures-functions-and-packages"></a>支援多載程序、 函數和封裝  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援由多載程序、 函數和封裝附加唯一字串的節點識別碼，它會呈現每個多載成品的命名空間。 此字串是下一個多載，等第一個多載中，「 overload2""overload1"。  
  
 WCF 服務模型中每個多載程序或函式會以唯一的 WCF 用戶端。 這點不同於在非多載的情況中所有結構描述時，所有結構描述中的程序中的函數或程序和函式，在封裝中的所有叫用之相同的 WCF 用戶端。 下表顯示 WCF 用戶端名稱和多載程序、 函式，以及封裝所產生的方法。  
  
|Oracle 成品|WCF 用戶端名稱|範例|  
|---------------------|---------------------|-------------|  
|多載的封裝 （程序）|[結構描述]封裝 [PACKAGE_NAME] [PROC_NAME]] [OVERLOAD_ID] 用戶端。[PROC_NAME]|SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC|  
|多載的封裝 （函式）|[結構描述]封裝 [PACKAGE_NAME] [FUNC_NAME]] [OVERLOAD_ID] 用戶端。[FUNC_NAME]|SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC|  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。  
  
 [FUNC_NAME] = Oracle 函式; 的名稱例如 MYFUNC。  
  
 [PACKAGE_NAME] = Oracle 封裝的名稱。  
  
 [OVERLOAD_ID] = 唯一的字串，識別多載的成品。「 overload1"、"overload2"，等等。  
  
 下表顯示多載程序、 函式，以及封裝所產生的命名空間。  
  
|Oracle 成品|命名空間|範例|  
|---------------------|---------------|-------------|  
|封裝 （程序）|[BASE_NS]。 [結構描述]。封裝。[PACKAGE_NAME]。[PROC_NAME][OVERLOAD_ID]|microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYPROC.overload1|  
|封裝 （函式）|[BASE_NS]。 [結構描述]。封裝。[PACKAGE_NAME]。[FUNC_NAME]。[OVERLOAD_ID]|microsoft.lobservices.oracledb._2007._03.SCOTT。Package.MYPACKAGE.MYFUNC.overload1|  
|一般記錄集 （弱型別）|[BASE_NS]|microsoft.lobservices.oracledb._2007._03|  
  
 [BASE_NS] = 的基底配接器命名空間中。microsoft.lobservices.oracledb._2007._03。  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [PROC_NAME] = Oracle 程序; 的名稱例如，MYPROC。  
  
 [FUNC_NAME] = Oracle 函式; 的名稱例如 MYFUNC。  
  
 [PACKAGE_NAME] = Oracle 封裝的名稱。  
  
 [OVERLOAD_ID] = 唯一的字串，識別多載的成品。「 overload1"、"overload2"，等等。 字串中的數值是 Oracle 資料庫所維護之成品的多載識別碼。  
  
 下列範例示範 WCF 用戶端和針對 ACCOUNT_PKG 封裝中的多載 GET_ACCOUNT 程序產生的方法簽章。 （Oracle 宣告會包含）。此範例示範如何產生唯一的 WCF 用戶端的每一個多載，以及如何針對每個用戶端產生該方法會傳回唯一的命名空間中設定的記錄。  
  
```  
/* Procedure that takes account ID and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aid IN account.acctid%TYPE, acct OUT account%ROWTYPE) ;  
  
/* Procedure that takes account name and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aname IN account.name%TYPE, acct OUT account%ROWTYPE) ;  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1.ACCTRECORD GET_ACCOUNT(System.Nullable<decimal> AID);  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2.ACCTRECORD GET_ACCOUNT(string ANAME);  
}  
```  
  
## <a name="invoking-functions-and-procedures"></a>叫用的函數和程序  
 要叫用函式或程序，使用 WCF 用戶端，執行下列步驟。  
  
1.  產生目標函式、 程序或封裝的 WCF 用戶端類別。 這個類別應該包含您將目標成品叫用作業的方法。  
  
    > [!NOTE]
    >  在[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，多載函式和程序會出現在**可用的類別和作業**為 [NAME].1，[NAME].2、.3、 [名稱] 方塊並依此類推，[NAME] 所在的多載的成品和數字的值名稱是 Oracle 資料庫上的多載識別碼。  
  
2.  建立 WCF 用戶端類別的執行個體並呼叫其方法來叫用的函式或程序。  
  
 如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[與 Oracle 資料庫配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的 Oracle 資料庫上執行交易內的每一項作業。  
  
> [!IMPORTANT]
>  唯一的命名空間中宣告的類別代表 REF CURSOR 和記錄型別參數或傳回值的函式或程序 （和封裝） 中的每個函式或程序。 這表示，例如，封裝 REF 資料指標類型做為傳回值會在兩個不同的函式宣告中唯一的命名空間時的每個 WCF 用戶端方法。 您可能必須宣告另一個變數來保存這些不同的傳回值，或當您叫用 WCF 用戶端方法的其中一個適當轉換變數。  
  
 下列範例示範如何呼叫取得帳戶記錄 /SCOTT/ACCOUNT 資料表中的多載的 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT 程序。 首先會建立新的記錄，藉由呼叫 /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT 程序。 然後讀取新的記錄備份兩次所呼叫的 GET_ACCOUNT 不同多載。 這個範例會使用三個 WCF 用戶端，一個用於 CREATE_ACCOUNT 程序，分別指派給 GET_ACCOUNT 多載。 別名用來區別 GET_ACCOUNT 傳回值使用的命名空間。 SDK 範例提供完整的範例。 如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// Alias client namespaces to shorten declarations of "shared" types   
using CREATE_ACCOUNTns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT;  
using GET_ACCOUNT_BY_IDns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1;  
using GET_ACCOUNT_BY_NAMEns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2;  
  
// This sample demonstrates calling overloaded packaged procedures on Oracle  
// First a new account is created by calling CREATE_ACCOUNT which takes two record parameters  
// Then the information for the new account is returned by calling an overloaded procedure GET_ACCOUNT  
// The first overload returns the account information by account ID  
// The second overload returns the account information by account name  
// Notice that different clients (and namespaces) are created for overloaded procedures and functions  
namespace OracleOverloadsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            decimal acctId;  
            string newAccountName = "Paula Bento";  
  
            Console.WriteLine("Creating clients");  
            // Create Client for CREATE_ACCOUNT Function  
            SCOTTPackageACCOUNT_PKGClient createAccountClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // NOTE: user name and password are case-sensitive  
            createAccountClient.ClientCredentials.UserName.UserName = "SCOTT";  
            createAccountClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 1 -- takes ACCOUNT ID parameter  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client getAccountByIdClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1");  
            // NOTE: user name and password are case-sensitive  
            getAccountByIdClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByIdClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 2 -- takes ACCOUNT NAME parameter  
            // NOTE: this client can be created from configuration; detail provided here  
            // for demonstration  
            OracleDBBinding overload2Binding = new OracleDBBinding();  
            EndpointAddress overload2EndpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client getAccountByNameClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client(overload2Binding, overload2EndpointAddress);  
            // NOTE: user name and password are case-sensitive  
            getAccountByNameClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByNameClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
                Console.WriteLine("Opening clients -- please wait");  
                // Open clients  
                createAccountClient.Open();  
                getAccountByIdClient.Open();  
                getAccountByNameClient.Open();  
  
                Console.WriteLine("Creating new account");  
                // Create an account record  
                // NOTE: ACCTRECORD is defined in all three namespaces so specify the definition  
                // that corresponds to the client.  
                CREATE_ACCOUNTns.ACCTRECORD acctRec = new CREATE_ACCOUNTns.ACCTRECORD();  
  
                // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
                acctRec.ACCTID = 0;  
                acctRec.NAME = newAccountName;  
                acctRec.BALANCE = 10537;  
  
                // Create address record  
                CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
                addrRec.STREET = "456 Valley Rd";  
                addrRec.CITY = "New York";  
                addrRec.STATE = "NY";  
  
                // Create account  
                acctId = (decimal)createAccountClient.CREATE_ACCOUNT(acctRec, addrRec);  
                Console.WriteLine("New Account Created: AccountId = {0}, Name = {1}, Balance = {2:C}",  
                   acctId, acctRec.NAME, acctRec.BALANCE);  
  
                /* Get new account by Id */  
                GET_ACCOUNT_BY_IDns.ACCTRECORD acctById = getAccountByIdClient.GET_ACCOUNT(acctId);  
                Console.WriteLine("Account Returned by Id: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctById.ACCTID, acctById.NAME, acctById.BALANCE);  
  
                /* Get new account by Name */  
                GET_ACCOUNT_BY_NAMEns.ACCTRECORD acctByName = getAccountByNameClient.GET_ACCOUNT(newAccountName);  
                Console.WriteLine("Account Returned by Name: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctByName.ACCTID, acctByName.NAME, acctByName.BALANCE);  
  
                Console.WriteLine("Hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close all the clients  
                createAccountClient.Close();  
                getAccountByIdClient.Close();  
                getAccountByNameClient.Close();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)