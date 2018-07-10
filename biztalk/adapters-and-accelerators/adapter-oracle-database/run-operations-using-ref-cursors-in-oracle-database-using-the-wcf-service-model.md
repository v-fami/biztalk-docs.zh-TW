---
title: 使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations using REF CURSORS
- REF CURSORS, performing operations
ms.assetid: b4cb9ede-eae1-44d7-8ba5-7e1261ccfa3b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c30af70ffe58e1ca8107c07d265e848532e2c768
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990703"
---
# <a name="run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model"></a>使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR
REF CURSOR 是 Oracle 的 PL/SQL 資料類型，表示結果集的 Oracle 資料庫中的指標。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援程序、 函數和封裝中的 REF CURSOR 參數。 REF CURSOR 參數可以是強型別或弱型別取決於程序或函式中的宣告方式。 如需詳細說明的 REF CURSOR 參數都由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [REF CURSORS 的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)。下表摘要說明如何將 REF CURSOR 參數表示 WCF 服務模型中。  
  
|參數方向|強型別 REF CURSOR|弱型別 REF CURSOR|  
|-------------------------|--------------------------------|------------------------------|  
|IN|`string [PARAM_NAME]`<br /><br /> 包含 PL/SQL 區塊的字串。 PL/SQL 區塊必須傳回開啟的 REF CURSOR，執行"開啟如 SELECT"陳述式或叫用函式或程序。 問號 （？） 指出傳回參數的 REF 資料指標的位置。 比方說，「 開始開啟？ 選取 * 從 MY_TABLE;END"或"BEGIN MY_PROC (PARM1，？，PARM2);結束; 」。|與強型別相同|  
|OUT|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> 強類型的記錄集。|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> 弱型別泛型記錄集。|  
|IN OUT|OUT REF CURSOR 參數會分成 IN 和 OUT 參數。 IN 參數會附加"_IN"中方法簽章，以區分它與 OUT 參數。 OUT 參數被以強類型的記錄集。<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|OUT REF CURSOR 參數會分成 IN 和 OUT 參數。 IN 參數會附加"_IN 」，以區分它與 OUT 參數。 OUT 參數被以弱式類型的記錄集。<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 [PARAM_NAME] = [Oracle 資料庫中; 函數或程序定義中參數的名稱比方說，MYREFCURSOR。  
  
 [PROC_NS] = 包含參數的封裝、 程序或函式; 產生的唯一命名空間例如，"microsoft.lobservices.oracledb._2007._03.SCOTT。Package.ACCOUNT_PKG。GET_ACTIVITY"。  
  
 [GENERIC_NS] = 命名空間中定義的是泛型的記錄集，「 microsoft.lobservices.oracledb._2007._03"。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會使用 SCOTT/封裝/ACCOUNT_PKG Oracle PACKAGE。 下列程序會使用從 ACCOUNT_PKG:  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 指令碼來產生此封裝提供 SDK 範例。 如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
## <a name="ref-cursor-parameters-in-the-wcf-service-model"></a>WCF 服務模型中的 REF CURSOR 參數  
 下列範例顯示的類別和 /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序所產生的 WCF 用戶端。 此程序具有弱式型別的 IN 和 OUT REF CURSOR 參數和強型別中出 REF CURSOR 參數。  
  
 以下是產生 WCF 用戶端來叫用 GET_ACTIVITY 中方法的簽章。  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 在  **GET_ACTIVITY**方法中，在 OUT 參數 INOUTRECS 會分割成兩個參數：  
  
- INOUTRECS_IN 是表示在 REF CURSOR 參數的字串。  
  
- INOUTRECS 是表示出 REF CURSOR 參數的強類型的記錄集。  
  
  弱型別 OUT 參數，OUTRECS，被以一組標準的記錄。 弱型別參數，INRECS 中, 會表示為字串。  
  
### <a name="strongly-typed-out-ref-cursor-parameters"></a>強型別 OUT REF CURSOR 參數  
 強型別外 （或在 OUT） REF CURSOR 參數會產生唯一的命名空間會根據結構描述、 套件和程序或函式中使用的名稱。 /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序中，這個命名空間是`microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`。 將具有 「 記錄 」 的參數名稱附加形成的類別名稱和類別由表示 Oracle 欄位的屬性所組成。 下面顯示的類別表示強型別產生記錄 INOUTRECS REF CURSOR 參數的一部分。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class INOUTRECSRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private System.Nullable<decimal> TIDField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public System.Nullable<decimal> TID {  
            get {  
                return this.TIDField;  
            }  
            set {  
                this.TIDField = value;  
            }  
        }  
  
        ...  
  
    }  
}  
```  
  
### <a name="weakly-typed-out-ref-cursor-parameters"></a>弱型別 OUT REF CURSOR 參數  
 弱型別外 （或在 OUT） REF CURSOR 參數都由一般記錄類別。 泛型的記錄集時，一定會產生相同的命名空間中，並使用相同的類別名稱，不論函式或程序。 下列程式碼會示範一般記錄類別**microsoft.lobservices.oracledb._2007._03.GenRecordRow**，用來表示 OUTRECS 出 SYS_REFCURSOR 參數 （弱型別） 的記錄。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordRow : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumnField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumn {  
            get {  
                return this.GenRecordColumnField;  
            }  
            set {  
                this.GenRecordColumnField = value;  
            }  
        }  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordColumn : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private string ColumnNameField;  
  
        private string ColumnValueField;  
  
        private string ColumnTypeField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false)]  
        public string ColumnName {  
            get {  
                return this.ColumnNameField;  
            }  
            set {  
                this.ColumnNameField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public string ColumnValue {  
            get {  
                return this.ColumnValueField;  
            }  
            set {  
                this.ColumnValueField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false, Order=2)]  
        public string ColumnType {  
            get {  
                return this.ColumnTypeField;  
            }  
            set {  
                this.ColumnTypeField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="using-ref-cursor-parameters-with-a-wcf-client"></a>使用 WCF 用戶端中的 REF CURSOR 參數  
 若要使用 WCF 用戶端，叫用的程序或使用 REF CURSOR 參數的函式，您執行下列作業：  
  
1. 將字串傳遞中為 for each 或 IN 出 REF CURSOR 參數，其中包含 PL/SQL 封鎖開啟 REF CURSOR。 此區塊可以執行在開啟的 SELECT 陳述式，或叫用的函式或程序，在 OUT 參數傳回開啟的 REF CURSOR。  
  
2. 當程序或函式傳回時，對中傳回的任何 OUT 或 IN 出 REF CURSOR 參數的資料錄集的資料。 一般記錄弱型別 REF CURSOR 參數的設定或設定強型別 REF CURSOR 參數的強型別的記錄，將會記錄集。  
  
   如需如何使用 WCF 服務模型，叫用程序和函數的詳細資訊，請參閱[叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。  
  
   下列範例會呼叫 GET_ACTIVITY 程序。 它會示範指定中 REF CURSOR 參數的兩種方式：  
  
- 中 REF CURSOR 參數，指定在開啟的 SELECT 陳述式傳回帳戶 100001 活動。  
  
- 在出 REF CURSOR 參數，會叫用 /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY 程序。 此程序會開啟一個 REF 資料指標，包含所有 ACCOUNTACTIVITY 資料表中的活動並將其傳回做為 OUT 參數。  
  
  此範例也會示範如何讀取從記錄集的強型別和弱型別 REF CURSOR 參數傳回的資料。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// namespaces for strongly-typed and weakly typed REF CURSOR records  
using GET_ACTIVITYns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY;  
using GENERICns = microsoft.lobservices.oracledb._2007._03;  
  
// In this sample, INRECS is opened by using an OPEN FOR statement, and  
// INOUTRECS_IN is opened by calling the GET_ALL_ACTIVITY procedure on Oracle.  
  
namespace OracleRefCursorsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the client  
            SCOTTPackageACCOUNT_PKGClient accountPkgClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // Set credentials  
            accountPkgClient.ClientCredentials.UserName.UserName = "SCOTT";  
            accountPkgClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
  
                GET_ACTIVITYns.INOUTRECSRECORD[] strongCursor;  
                GENERICns.GenRecordRow[] weakCursor;  
  
                Console.WriteLine("Opening client");  
                // Open the client  
                accountPkgClient.Open();  
  
                Console.WriteLine("Invoking ACCOUNT_PKG.GET_ACTIVITY");  
                // Get  ACCOUNTACTIVITY records  
                // The IN REF CURSOR is set to all activity for account 100001  
                // The input part of the IN OUT ref cursor calls GET_ALL_ACTIVITY  
                // The weakly-typed OUT REF CURSOR parameter returns a list of activity for account 100001  
                // The strongly-typed IN OUT REF CURSOR parameter returns a list of all activity  
                string inRecsString = "BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;";  
                string inoutRecsString = "BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;";  
  
                accountPkgClient.GET_ACTIVITY(  
                                inRecsString,  
                                inoutRecsString,  
                                out strongCursor,  
                                out weakCursor);  
  
                // Display strong ref cursor (all activity)  
                Console.WriteLine("\nList of all activity returned (strong ref cursor)");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < strongCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2:C}\t{3}\t{4}",strongCursor[i].TID,  
                        strongCursor[i].ACCOUNT,   
                        strongCursor[i].AMOUNT,   
                        strongCursor[1].TRANSDATE,  
                        strongCursor[i].DESCRIPTION);  
                }  
  
                // Display weak ref cursor (account 100001)  
                Console.WriteLine("\nList of activity for account 100001 returned (weak ref cursor)");  
                Console.WriteLine("Tx Id\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < weakCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1:C}\t{2}\t{3}", weakCursor[i].GenRecordColumn[0].ColumnValue,  
                        weakCursor[i].GenRecordColumn[2].ColumnValue,  
                        weakCursor[i].GenRecordColumn[4].ColumnValue,  
                        weakCursor[i].GenRecordColumn[3].ColumnValue);  
                }  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
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
                // Close the client  
                accountPkgClient.Close();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)