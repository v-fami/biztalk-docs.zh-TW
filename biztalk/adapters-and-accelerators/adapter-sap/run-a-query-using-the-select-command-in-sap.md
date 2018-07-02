---
title: 在 SAP 中使用 SELECT 命令執行查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SELECT command, performing a query
- query, performing by using the SELECT command
ms.assetid: 6f03243c-ef50-4a4a-8fe6-4e525bd7efe3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5e4edb19c3f69b14dd55219f504a6a3d0cc1688
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971079"
---
# <a name="run-a-query-using-the-select-command-in-sap"></a>在 SAP 中使用 SELECT 命令執行查詢
[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]公開為 ADO.NET 資料來源的 SAP 系統。 使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，您可以執行 SELECT 陳述式來查詢 SAP 成品。  
  
## <a name="how-to-perform-a-query-by-using-the-select-command"></a>如何使用 SELECT 命令執行查詢  
 若要使用的查詢 SAP 成品[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，執行下列步驟：  
  
#### <a name="to-perform-a-query"></a>若要執行查詢  
  
1. 包含的參考 (和程式碼中使用陳述式) 來**Microsoft.Data.SAPClient**。  
  
2. 建立**SAPConnection** SAP 連接字串中使用資料提供者的物件。 如需有關連接字串的詳細資訊，請參閱 <<c0> [ 閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
3. 開啟 SAP 系統的連線，藉由叫用**開放**上**SAPConnection**。  
  
4. 建立**SAPCommand**物件**SAPConnection**。  
  
5. 指定的 SELECT 陳述式**CommandText**屬性**SAPCommand**。 如果有必要，您可以指定使用的參數**SAPParameter**物件。 如需如何查詢使用 SELECT 陳述式的 SAP 成品的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。 如需如何指定 BAPI 或 RFC 的範例，請參閱[SELECT 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md)。  
  
6. 執行命令，以執行查詢並取得結果**SAPDataReader**。  
  
7. 讀取從結果**SAPDataReader**。  
  
8. 當您完成使用它們時，關閉 （或 dispose） **SAPConnection**並**SAPDataReader**。  
  
   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]也會公開**SAPClientFactory**類別，可用來建立**SAPConnection**， **SAPCommand**和**SAPConnection**物件。 如需有關 ADO.NET 類別來擴充[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱 <<c2> [ 與 SAP 配接器擴充 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)。  
  
## <a name="example"></a>範例  
 下列範例會寫入至主控台的參數化的內部聯結陳述式的 select 的結果。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoSelect  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        /// <summary>  
        /// select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid  
        /// </summary>  
  
        string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid";  
                    cmd.Parameters.Add(new SAPParameter("@connid", 17));                      
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
                                    b.Append(dr[i].ToString()+" ");  
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
 [範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)