---
title: 建立 MSMQ 接收位置和傳送埠從程式碼 |Microsoft 文件
description: 以程式設計方式建立 MSMQ 接收位置和 BizTalk Server 中的傳送埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ebb4119-deeb-4287-aa65-7597ff0cc435
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f00a0bfe14eeb7d4205973b3fef96e23026616
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971668"
---
# <a name="create-msmq-receive-locations-and-send-ports-programmatically"></a>以程式設計方式建立 MSMQ 接收位置和傳送埠
本主題將說明如何使用 WMI 來建立 MSMQ 配接器的連接埠或位置。  
  
 如需詳細資訊，請參閱**與日期時間排程組態使用 WMI 建立接收位置** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="setting-property-values"></a>設定屬性值  
 建立連接埠或位置的程序都是相同的：  
  
1.  建立正確型別的物件。  
  
2.  設定物件的屬性值。  
  
3.  認可物件值到資料庫。  
  
 所有介面卡都有特定的屬性，例如**HostName**通用。 您可以用直接指派到物件的方式來設定這些通用屬性。 以下 C# 程式碼所示就是這種典型範例：  
  
```  
objReceiveLocation["HostName"] = "BizTalkServerApplication";  
```  
  
 您為非所有配接器所共用的屬性指派值。 您用字串建立 XML 文件，並將該字串指派給 CustomCfg 屬性。 以下 C# 程式碼所示就是典型的 FILE 配接器範例：  
  
```  
objReceiveLocation["CustomCfg"] =   
        @"<CustomProps>"  
        + @"<BatchSize>20</BatchSize>"  
        + @"<FileMask>*.xml</FileMask>"  
        + @"<FileNetFailRetryCount>5</FileNetFailRetryCount>"  
        + @"<FileNetFailRetryInt>5</FileNetFailRetryInt>"  
        + @"</CustomProps>";  
```  
  
 在 CustomProps 項目內標記的名稱，就是配接器會用於這些屬性的內部名稱。  
  
 MSMQ 配接器在 CustomProps 標記中設有單一個 AdapterConfig 標記。 AdapterConfig 標記包含已括在 Config 標記中之自訂屬性值會使用的 XML 標記字串。 不過，標記會編碼:"&lt;"取代"\<"和"&gt;"取代"\>"。 例如，用於 MSMQ 屬性之配接器子集的 XML 可能如下所示：  
  
```  
<Config>  
    <batchSize>40</batchSize>  
</Config>  
```  
  
 請注意， **vt**屬性不是。 指派給字串**CustomCfg**屬性編碼後顯示如下：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config><batchSize>40</batchSize></Config></AdapterConfig></CustomProps>  
```  
  
## <a name="custom-property-names"></a>自訂屬性名稱  
 下表描述的 MSMQ 配接器的內部名稱**傳送**自訂屬性。  
  
|**傳送自訂屬性名稱**|**顯示名稱**|  
|-----------------------------------|----------------------|  
|acknowledgeType|通知類型|  
|administrationQueue|管理佇列|  
|憑證 (certificate)|憑證指紋|  
|encryptionAlgorithm|加密演算法|  
|maximumMessageSize|訊息大小上限 (以 KB 為單位)|  
|密碼|密碼|  
|priority|訊息優先順序|  
|queue|目的地佇列|  
|recoverable|可復原|  
|segmentationSupport|支援分割|  
|sendBatchSize|批次大小|  
|sendQueueName|目的地佇列|  
|timeOut|逾時|  
|timeOutUnits|逾時單位|  
|transactional|異動|  
|useAuthentication|使用驗證|  
|useDeadLetterQueue|使用無法寄出的信件佇列|  
|useJournalQueue|使用日誌佇列|  
|userName|使用者名稱|  
  
 下表描述的 MSMQ 配接器的內部名稱**接收**自訂屬性。  
  
|**Receive 自訂屬性名稱**|**顯示名稱**|  
|--------------------------------------|----------------------|  
|batchSize|批次大小|  
|密碼|密碼|  
|佇列|佇列|  
|serialProcessing|連續處理|  
|異動|異動|  
|userName|使用者名稱|  
  
## <a name="sample-code"></a>範例程式碼  
 以下 C# 程式會針對 MSMQ 配接器建立單一個接收位置。 它會假設接收埠 ReceivePort1 存在，並且使用 Helper 函式來將這些自訂屬性編碼和格式化。  
  
```  
using System;  
using System.Management;  
using System.Text;  
  
namespace CreateReceive  
{  
    ///   
    /// Program to create a receive location.  
    ///   
    class CreateReceive  
    {  
        /// The main entry point for the application.  
  
        [STAThread]  
        static void Main()  
        {  
            // Custom properties & values  
            string cfg =   
                    @"<queue>FORMATNAME:DIRECT=OS:MYMACHINE02\PRIVATE$\QUEUE2</queue>"  
                    + @"<batchSize>40</batchSize>"  
                    + @"<transactional>true</transactional>"  
                    + @"<serialProcessing>false</serialProcessing>";  
  
            CreateReceiveLocation (  
                    "Code Created Location",  
                    "ReceivePort1",  
                    "MSMQ",  
                    "BizTalkServerApplication",  
                    EncodeCustomProps(cfg),  // Encode the custom props  
                    "Microsoft.BizTalk.DefaultPipelines.PassThruReceive,"   
                            + " Microsoft.BizTalk.DefaultPipelines,"   
                            + " Version=3.0.1.0, Culture=neutral,"   
                            + " PublicKeyToken=31bf3856ad364e35",  
                    @"FORMATNAME:DIRECT=OS:MYMACHINE\PRIVATE$\QUEUE2"  
                );  
  
        }  
  
        static string EncodeCustomProps (string cp) {  
  
            // Enclose the properties and values in a Config> tag.  
            StringBuilder tmp = new StringBuilder( @"<Config>" + cp + @"</Config>");  
  
            // Encode the string  
            tmp = tmp.Replace("<","<");  
            tmp = tmp.Replace(">",">");  
  
            return (  
                // Enclose the encoded string with necessary tags  
                "<CustomProps><AdapterConfig vt=\"8\">"  
                + tmp.ToString()   
                + "</AdapterConfig></CustomProps>");  
  
        }  
  
        static void CreateReceiveLocation (  
            string name,            // Location name  
            string port,            // Receive port, already exists  
            string adapterName,     // The transport type  
            string hostName,        // BTS host  
            string customCfg,       // Encoded custom properties  
            string pipeline,        // Full specification of pipeline  
            string inboundTransport)// Inbound transport url  
        {  
            try   
            {  
                // Create options to store options in management object  
                PutOptions options = new PutOptions();  
                options.Type = PutType.CreateOnly;  
  
                // Create a management object  
                // Get the class  
                ManagementClass objReceiveLocationClass =   
                           new ManagementClass(  
                               "root\\MicrosoftBizTalkServer",   
                               "MSBTS_ReceiveLocation",   
                               null);  
                // Create an instance of the member of the class  
                ManagementObject objReceiveLocation =  
                          objReceiveLocationClass.CreateInstance();  
  
                // Fill in the properties  
                objReceiveLocation["Name"] = name;  
                objReceiveLocation["ReceivePortName"] = port;  
                objReceiveLocation["AdapterName"] = adapterName;  
                objReceiveLocation["HostName"] = hostName;  
                objReceiveLocation["PipelineName"] = pipeline;  
                objReceiveLocation["CustomCfg"] = customCfg;  
                objReceiveLocation["IsDisabled"] = true;  
                objReceiveLocation["InBoundTransportURL"] = inboundTransport;  
  
                // Put the options -- creates the receive location  
                objReceiveLocation.Put(options);  
            }  
            catch (Exception excep)  
            {  
                System.Console.WriteLine("Create Receive Location ({0}) failed - {1}",  
                                                name, excep.Message);  
            }  
        }  
    }  
}  
```