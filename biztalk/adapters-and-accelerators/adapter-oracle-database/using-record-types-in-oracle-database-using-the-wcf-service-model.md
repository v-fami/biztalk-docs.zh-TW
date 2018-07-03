---
title: 使用 WCF 服務模型的 Oracle 資料庫中執行作業使用的記錄類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD types, performing operations
- WCF service model, performing operations using RECORD types
ms.assetid: e7118a86-7470-48bb-aca0-6200dc0bb67c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd9bda9fc560310a882c5d48117cd823d544453
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004471"
---
# <a name="run-operations-using-record-types-in-oracle-database-using-the-wcf-service-model"></a>使用 WCF 服務模型的 Oracle 資料庫中執行作業使用的記錄類型
Oracle 記錄類型用來代表階層式參數傳遞至 PL/SQL 函數與程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現複雜的 XML 類型的記錄類型。 在 WCF 服務模型中，會還原序列化為強型別.NET 類別的記錄類型。 記錄欄位會表示為類別的屬性。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：  
  
- 記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。  
  
- 例如，宣告為類型的記錄參數的 PL/SQL 封裝中的記錄類型 `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`  
  
- 包含巢狀的記錄的記錄類型。  
  
- 記錄中出現的類型為，縮小或在 OUT 參數至程序或函式。  
  
- 是函式傳回值的記錄類型。  
  
  本主題說明如何在 WCF 服務模型中表示記錄類型。 如需如何呼叫 Oracle 程序和函式的資訊，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會使用 SCOTT/ACCOUNT_PKG Oracle 的 PL/SQL 封裝。 下列項目會使用從 ACCOUNT_PKG。  
  
```  
TYPE address_rec_type IS RECORD (street customer.street%TYPE, city customer.city%TYPE, state customer.state%TYPE);  
  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
  
TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);  
  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
```  
  
 指令碼來產生此封裝提供給[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 如需詳細資訊，請參閱指令碼  
  
 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="record-types-in-the-wcf-service-model"></a>WCF 服務模型中的記錄類型  
 Oracle 記錄類型以複雜的 XML 型別，由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 在 WCF 服務模型中，複雜的 XML 型別都由一個類別，而這個類別的屬性則代表 Oracle 記錄類型的欄位。 封裝 （如果有的話） 和函式或程序的結構描述會限定命名空間中產生的類別，表示記錄型別參數。 函式或程序的參數，可唯一識別此命名空間。 例如，下列命名空間中建立 Oracle 封裝 ACCOUNT_PKG CREATE_ACCOUNT 程序的記錄型別參數： `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`。 如需 WCF 服務模型中，用以代表程序和函式中的複雜類型的命名空間的詳細資訊，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
 記錄型別參數的命名空間由程序或函式，而記錄型別參數所產生之類別的名稱是記錄型別宣告決定附帶一提。 下表顯示產生的類別名稱的方式根據宣告 Oracle 記錄型別參數的兩種不同的方式。  
  
|Oracle 記錄類型|[屬性]|範例|  
|------------------------|----------|-------------|  
|資料表 %rowtype 程序或函式參數|[P]記錄|ACCTRECORD|  
|記錄封裝參數的型別|[PACKAGE_NAME][RECORD_TYPE_NAME]記錄|ACCOUNT_PKGACCTINFO_REC_TYPERECORD|  
  
 [P] = 程序或函式參數名稱;比方說，ACCT  
  
 [PACKAGE_NAME] = Oracle 封裝的名稱。  
  
 [RECORD_TYPE_NAME] = 記錄類型宣告中指定的名稱比方說，ACCTINFO_REC_TYPE。  
  
 下列程式碼會顯示為兩個 Oracle 函式產生 WCF 用戶端的方法簽章。 /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT 函式會採用兩個簡單的記錄類型 IN 參數，並 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO 函式會傳回包含兩個巢狀的記錄類型的記錄型別參數。 Oracle 函式宣告會包含在程式碼頂端項目。 每個函式的參數是由唯一的命名空間限定的。  
  
```  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
  
public partial class SCOTTPackageACCOUNT_PKGClient : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKG>, SCOTTPackageACCOUNT_PKG {  
  
    ...  
  
    public System.Nullable<decimal> CREATE_ACCOUNT(microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD ACCT, microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDR);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD GET_ACCOUNTINFO(System.Nullable<decimal> AID);  
}  
```  
  
 下列程式碼顯示針對 CREATE_ACCOUNT 函式的參數產生的類別： `FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`  
  
 此函式具有資料表 %資料列型別以宣告的參數和宣告類型的記錄套件類型的參數 (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`)。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT {  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGADDRESS_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
}  
```  
  
### <a name="representation-of-a-simple-record-type"></a>簡單的記錄類型表示法  
 下列程式碼示範如何在 WCF 服務模型中表示簡單的記錄類型。 此程式碼顯示展開之檢視的**ACCOUNTRECORD**代表 CREATE_ACCOUNT 函式中的帳戶 %資料列型別參數的類別。 在這個類別中的記錄欄位 （資料列資料行） 會表示為屬性。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Runtime.Serialization.DataContractAttribute()]  
public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
    private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
    private System.Nullable<decimal> ACCTIDField;  
  
    private string NAMEField;  
  
    private System.Nullable<decimal> BALANCEField;  
  
    public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
        get {  
            return this.extensionDataField;  
        }  
        set {  
            this.extensionDataField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public System.Nullable<decimal> ACCTID {  
        get {  
            return this.ACCTIDField;  
        }  
        set {  
            this.ACCTIDField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public string NAME {  
        get {  
            return this.NAMEField;  
        }  
        set {  
            this.NAMEField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute(Order=2)]  
    public System.Nullable<decimal> BALANCE {  
        get {  
            return this.BALANCEField;  
        }  
        set {  
            this.BALANCEField = value;  
        }  
    }  
}  
```  
  
### <a name="representation-of-a-record-type-that-contains-nested-records"></a>包含巢狀的記錄的記錄類型的表示法  
 下列程式碼顯示包含巢狀的記錄的記錄類型的表示法。 這個特定記錄類型是 GET_ACCOUNTINFO 函式的傳回值 (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`)。 ACCTINFO_REC_TYPE 為封裝參數，使用一種類型的記錄建構宣告 (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`)。 它包含兩個巢狀的簡單記錄類型，資料表 %的資料列記錄和套件類型的記錄。 這些兩個簡單的記錄會在其父記錄相同的命名空間中宣告，並遵照預期的命名慣例。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGACCTINFO_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCTField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESSField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCT {  
            get {  
                return this.ACCTField;  
            }  
            set {  
                this.ACCTField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESS {  
            get {  
                return this.ADDRESSField;  
            }  
            set {  
                this.ADDRESSField = value;  
            }  
        }  
    }  
```  
  
## <a name="using-record-types-in-your-code"></a>在您的程式碼中使用記錄類型  
 在您的程式碼中使用記錄類型很簡單。 要叫用程序或函式記錄型別參數，您會建立記錄類型或類型的執行個體，並在 WCF 用戶端上將其傳遞至適當的方法。 當程序或函式會傳回，您可以閱讀任何外的屬性，或在 OUT 參數或函式傳回值會宣告為記錄類型。 如需如何使用 WCF 服務模型，叫用程序和函數的詳細資訊，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
> [!IMPORTANT]
>  Oracle 記錄型別參數 （和函式會傳回） 會限定的命名空間及其函式或程序 （和封裝）。 這表示會在兩個不同的程序或函數的記錄類型會有不同的命名空間，針對每個程序或函式。 您必須確定當您使用特定的程序或函式時，正確地限定記錄類型。 比方說，封裝記錄型別 （記錄類型的宣告），可做為 IN 參數，兩個不同的函式會使用每個宣告對應至每個函式所產生的唯一命名空間宣告兩次相同的 WCF 用戶端程式碼。 您必須確定您傳遞給每個個別的函式的參數上使用正確的命名空間。  
  
 在下列範例中，CREATE_ACCOUNT 函式會呼叫具有兩個簡單的記錄參數。 接下來，會呼叫 GET_ACCOUNTINFO 函式。 此函數會傳回包含巢狀的記錄的記錄類型。 選取的欄位值從傳回的記錄會寫入至主控台。 此範例中會省略步驟來設定的 Oracle 資料庫的認證，並開啟 WCF 用戶端。  
  
```  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
…  
  
// Create the client from configuration  
using (SCOTTPackageACCOUNT_PKGClient accountPkgClient = new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG"))  
{  
  
    ...  
  
    decimal acctId;  
  
    // Create an account record  
    // Note: ACCTRECORD is defined in both namespaces so specify the definition  
    // that corresponds to the client.  
  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD acctRec =   
        new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD();  
  
    // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
    acctRec.ACCTID = 0;  
    acctRec.NAME = "Anton Kirilov";  
    acctRec.BALANCE = 9583;  
  
    // Create address record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
    addrRec.STREET = "234 Main St";  
    addrRec.CITY = "Boston";  
    addrRec.STATE = "MA";  
  
    // Create account  
    try  
    {  
        acctId = (decimal)accountPkgClient.CREATE_ACCOUNT(acctRec, addrRec);  
    }  
    catch (Exception ex)  
    {  
        // handle exception  
        ...  
    }  
  
    ...  
  
    // Account info record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD acctInfo =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD();  
  
    // Get account info for the account just created  
    // acctInfo is returned as a nested record type  
    try  
    {  
     acctInfo = accountPkgClient.GET_ACCOUNTINFO(acctId);  
    }  
    catch (Exception ex)  
    {  
    // handle exception  
    ...  
    }  
  
    // Write the account info to the console  
    Console.WriteLine("The account info is:");  
    Console.WriteLine("Name:\t\t\t{0}", acctInfo.ACCT.NAME);  
    Console.WriteLine("Street:\t\t\t{0}", acctInfo.ADDRESS.STREET);  
    Console.WriteLine("City:\t\t\t{0}", acctInfo.ADDRESS.CITY);  
    Console.WriteLine("State:\t\t\t{0}", acctInfo.ADDRESS.STATE);  
    Console.WriteLine("Account Id:\t\t{0}", acctInfo.ACCT.ACCTID);  
    Console.WriteLine("Account Balance:\t{0:C}", acctInfo.ACCT.BALANCE);  
  
    Console.WriteLine("\nHit <RETURN> to finish");  
    Console.ReadLine();  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)