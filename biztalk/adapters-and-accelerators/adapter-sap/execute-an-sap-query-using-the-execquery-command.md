---
title: "執行使用 EXECQUERY 命令 SAP 查詢 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520153bf-9477-4b35-8953-3f5cb444ab9f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86159a03858ae5aa31bb37da56b6e5ea68dac3ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="execute-an-sap-query-using-the-execquery-command"></a>執行 SAP 查詢使用 EXECQUERY 命令
[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]公開為 ADO.NET 資料來源的 SAP 系統。 與[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，您也可以執行 EXECQUERY 陳述式在 SAP 系統中執行預先定義的查詢。  
  
## <a name="how-to-perform-a-query-by-using-the-execquery-command"></a>如何使用 EXECQUERY 命令執行查詢  
 若要執行預先定義的 SAP 查詢使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，執行下列步驟：  
  
#### <a name="to-perform-a-query"></a>若要執行查詢  
  
1.  包含的參考 (與您的程式碼中使用陳述式) 以**Microsoft.Data.SAPClient**。  
  
2.  建立**SAPConnection** SAP 連接字串中使用資料提供者的物件。 如需有關連接字串的詳細資訊，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
3.  開啟 SAP 系統的連線，藉由叫用**開啟**上**SAPConnection**。  
  
4.  建立**SAPCommand**物件從**SAPConnection**。  
  
5.  指定的 EXECQUERY 陳述式中**CommandText**屬性**SAPCommand**。 如果有必要，您可以指定參數使用**SAPParameter**物件。 如需如何執行 SAP 系統使用 EXECQUERY 陳述式中定義查詢的詳細資訊，請參閱[sap EXECQUERY 陳述式語法](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md)。  
  
6.  執行命令，以執行查詢並取得結果**SAPDataReader**。  
  
7.  了解從結果**SAPDataReader**。  
  
8.  當您完成使用它們時，關閉 （或處置） **SAPConnection**和**SAPDataReader**。  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]也會公開**SAPClientFactory**類別，可用來建立**SAPConnection**， **SAPCommand**和**SAPConnection**物件。 如需有關 ADO.NET 類別透過擴充[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[擴充 SAP 配接器使用的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)。  
  
## <a name="example"></a>範例  
 下列範例會將查詢的結果，ZTEST1，寫入主控台。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExecQuery  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
           string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "EXECQUERY ZTEST1 @userGRoup='SYSTQV000024',@P1='0000001390',@P2='0000080150'";  
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