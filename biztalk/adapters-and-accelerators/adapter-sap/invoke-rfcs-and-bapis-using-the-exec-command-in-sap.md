---
title: 叫用 Rfc 和 Bapi SAP 中使用 EXEC 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EXEC command, invoking RFCs and BAPIs
- BAPIs and RFCs, invoking by using the EXEC command
- RFCs and BAPIs, invoking by using the EXEC command
ms.assetid: 55443679-2fa8-4c13-ac3b-1c85b5166cd2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 500e0f932a8245f76954aa7a8785dbec012321e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217214"
---
# <a name="invoke-rfcs-and-bapis-using-the-exec-command-in-sap"></a>叫用 Rfc 和 Bapi SAP 中使用 EXEC 命令
[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]公開為 ADO.NET 資料來源的 SAP 系統。 使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，您可以叫用 Rfc 和 Bapi EXEC 命令透過 SAP 系統上。  
  
## <a name="how-to-invoke-rfcs-and-bapis-on-the-sap-system"></a>如何叫用 Rfc 和 Bapi SAP 系統上  
 要叫用 RFC 或 BAPI 使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，執行下列步驟：  
  
#### <a name="to-invoke-an-rfc-or-bapi"></a>要叫用 RFC 或是 BAPI  
  
1.  包含的參考 (與您的程式碼中使用陳述式) 以**Microsoft.Data.SAPClient**。  
  
2.  建立**SAPConnection** SAP 連接字串中使用資料提供者的物件。 如需有關連接字串的詳細資訊，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
3.  開啟 SAP 系統的連線，藉由叫用**開啟**上**SAPConnection**。  
  
4.  建立**SAPCommand**物件從**SAPConnection**。  
  
5.  指定中的 BAPI 或 RFC 呼叫**CommandText**屬性**SAPCommand**。 如果有必要，您可以指定參數使用**SAPParameter**物件。 如需如何指定 BAPI 或 RFC 呼叫使用 EXEC 陳述式的詳細資訊，請參閱[sap EXEC 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md)。 如需如何指定 RFC 或 BAPI 的範例，請參閱[EXEC 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md)。  
  
6.  執行命令，以叫用 RFC 或 BAPI 並取得結果**SAPDataReader**。  
  
7.  了解從結果**SAPDataReader**。  
  
8.  當您完成使用它們時，關閉 （或處置） **SAPConnection**和**SAPDataReader**。  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]也會公開**SAPClientFactory**類別，可用來建立**SAPConnection**， **SAPCommand**和**SAPConnection**物件。 如需有關 ADO.NET 類別透過擴充[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[擴充 SAP 配接器使用的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)。  
  
## <a name="example"></a>範例  
 下列範例會叫用 SD_RFC_CUSTOMER_GET 擷取其名稱開頭為"AB"的所有客戶的客戶資訊。 它然後客戶將記錄寫入至主控台。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExec  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string connstr = "TYPE=A; ASHOST=YourSAPHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
            using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "exec sd_rfc_customer_get @name1='AB*' ";  
                    using (SAPDataReader dr = cmd.ExecuteReader())  
                    {  
                        do  
                        {  
                            int rows = 0;  
                            while (dr.Read())  
                            {  
                                rows++;  
                                StringBuilder b = new StringBuilder();  
                                for (int i = 0; i < dr.FieldCount; i++)  
                                {  
                                    b.Append(dr[i].ToString() + " ");  
                                }  
                                Console.WriteLine("row {0}: {1} ", rows, b.ToString());  
                            }  
                            Console.WriteLine("Number of rows:{0}", rows);  
                        } while (dr.NextResult());  
  
                    }  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)   
 [範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)