---
title: 從協調流程 」 範例執行的標頭屬性的存取權 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2059eb2c-50a3-4618-a6ec-faa1a9e5d368
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ddbb2ea7ef978c0e5eae07835d5a9c1320bbc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294774"
---
# <a name="running-the-header-property-access-from-an-orchestration-sample"></a>從協調流程 」 範例執行標頭屬性存取
範例的這個部分會示範如何 ESB 升級至訊息內容屬性，程式碼與在 Microsoft BizTalk 協調流程中的元件可以存取的 JMS 標頭的中繼資料。 此範例包含接收管線，其中包含將 JMS 標頭的中繼資料升級至訊息內容屬性 ESB JMS 元件的執行個體。  
  
 接收埠會從訊息內容屬性，將訊息傳遞至協調流程擷取佇列名稱的具名的 JMSRouter 指派 RfhUtil 公用程式 （和中繼資料標頭中傳送）。 協調流程會將此佇列名稱指派給動態傳送埠，並將訊息傳送到該連接埠。  
  
 連接埠的傳送管線包含將訊息內容屬性降級至 JMS 標頭中繼資料的 ESB JMS 元件的執行個體。  
  
 **若要執行標頭屬性存取範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
2.  執行 IBM RfhUtil 公用程式。選取名為 ESB 的佇列管理員。JMS。Sample.QueueManager 連接到此佇列管理員 中，如這個範例的第 1 部分所示的第一個下拉式清單。  
  
3.  在第二個下拉式清單中，選取名為 ESB 目標輸出佇列。JMS。範例。SENDTOBIZTALK。  
  
4.  按一下**ReadFile**按鈕 RfhUtil 公用程式中，然後巡覽至名為測試 000128 測試訊息檔案。JMS 位於子資料夾名為 \Source\Samples\JMS\Test\Data\Load\\。 此檔案包含 128 測試訊息批次，但是此公用程式載入只有第一個。  
  
5.  按一下**RFH**索引標籤，然後確定只有**JMS**選取核取方塊。  
  
6.  按一下**jms**索引標籤，並請確定所選**回覆**佇列是 ESB。JMS。範例。回覆，所選**目的地佇列**是 ESB。JMS。範例。DYNAMICQ2。  
  
7.  按一下**Main**索引標籤，然後再按一下**寫入 Q**  按鈕，將訊息寫入佇列。  
  
8.  在延遲之後應用程式執行，而 ESB 輸出訊息會出現在 ESB。JMS。範例。DYNAMICQ2 佇列。 開啟 WebSphere 佇列總管並瀏覽佇列，確認這個項目。  
  
## <a name="how-the-sample-works"></a>範例的運作方式  
 在協調流程中，程式碼可以存取 JMS 標頭中所載入到訊息的值**XmlDocument**執行個體，如下列程式碼所示。  
  
```csharp  
if (null != InboundMsg(  
    Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData))  
{     
  jmsInfo.LoadXml(InboundMsg(  
     Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData));  
  if (null != jmsInfo)  
  {  
    if (null != jmsInfo.SelectSingleNode("//Dst"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Dst");  
      destinationQueue = xElement.InnerText.ToUpper(  
                         System.Globalization.CultureInfo.CurrentCulture);  
    }  
    if (null != jmsInfo.SelectSingleNode("//Rto"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Rto");  
      replyToQueue = xElement.InnerText.ToUpper(  
                     System.Globalization.CultureInfo.CurrentCulture);  
    }  
  }  
}  
```  
  
 此外，程式碼可以存取的所有訊息的 MQMD 內容屬性。