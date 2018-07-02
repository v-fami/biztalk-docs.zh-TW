---
title: 支援 Windows SharePoint Services 資料行類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], supported column types
- Windows SharePoint Services adapters, supported column types
ms.assetid: 14992f52-9d18-4321-9152-83c8a37751bc
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f2f62709cf1d8c552d5f60c1ec9e7fbe627f8d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966719"
---
# <a name="supported-windows-sharepoint-services-column-types"></a>支援的 Windows SharePoint Services 資料行類型
本主題描述 Windows SharePoint Services 配接器支援的 Windows SharePoint Services 資料行類型。 這些資料行類型的值可以在訊息中設定。  

> [!NOTE]
>  配接器不會更新計算的資料行。  

## <a name="supported-types"></a>支援的類型  
 下表描述支援的資料行類型：  


|           UI 類型           | SharePoint 物件模型類型 |                    範例                    |                                                                                                                                                                                                                                                                            註解                                                                                                                                                                                                                                                                            |
|-----------------------------|------------------------------|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     單行文字     |       SPFieldType.Text       |                 單行                  |                                                                                                                                                                                                                                                                              無                                                                                                                                                                                                                                                                              |
|   多行文字    |       SPFieldType.Note       | 第 1 行<br /><br /> 第 2 行<br /><br /> 第 3 行 |                                                                                                                                                                                                                                                                              無                                                                                                                                                                                                                                                                              |
|      選擇下拉式       |      SPFieldType.Choice      |                   ChoiceA                    |                                                                                                                                                                                                                                                 從可用選項選擇的 ChoiceA (ChoiceA、ChoiceB、ChoiceC)                                                                                                                                                                                                                                                 |
|    選擇選項按鈕     |      SPFieldType.Choice      |             #ChoiceB;#ChoiceC;#              |                                                                                                                                                                                                                 已啟用 ChoiceB 與 ChoiceC，已停用 ChoiceA (可用的選項是 ChoiceA、ChoiceB、ChoiceC)。 使用 ;# 做為分隔符號。                                                                                                                                                                                                                 |
|           Number            |      SPFieldType.Number      |                   123.456                    |                                                                                                                                                                                                                                                                              無                                                                                                                                                                                                                                                                              |
| 美金貨幣 (或任何其他) |     SPFieldType.Currency     |                    100.00                    |                                                                                                                                                                                                                                                                              無                                                                                                                                                                                                                                                                              |
|           查閱            |      SPFieldType.Lookup      |                      @shouldalert                       |                                                                                                                                                                                                                                                 此號碼是參考清單內的項目識別項。                                                                                                                                                                                                                                                  |
|            YesNo            |     SPFieldType.Boolean      |                      @shouldalert                       |                                                                                                                                                                                                                                                                     1=Yes<br /><br /> 0=No                                                                                                                                                                                                                                                                     |
|    超連結或圖片     |       SPFieldType.URL        | http://www.microsoft.comMicrosoft 網站上 |                                                                                                                                                                                                                  以 "," 分隔 URL 與顯示文字。 「 Microsoft 網站 」 文字會靠的超連結 http://www.microsoft.com                                                                                                                                                                                                                   |
|        日期及時間        |     SPFieldType.DateTime     |             2005-02-11T10:05:04              | XML 標準為 xs:dateTime 定義的 DateTime。 dateTime 的格式是 CCYY-MM-DDThh:mm:ss，其中 CC 代表世紀，YY 代表年，MM 代表月，DD 則代表日，在此時間的前面會加上選用的前置負號 (-) 字元以表示負數。 若省略負號字元，就假定是正號 (+)。 T 是日期/時間的分隔符號，而 hh、mm 及 ss 分別代表時、分及秒。 此表示法可能緊接著 "Z" 以表示 UTC 或表示時區。 |

## <a name="see-also"></a>另請參閱  
 [如何設定 Windows SharePoint Services 接收位置](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [如何設定 Windows SharePoint Services 傳送處理常式](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)