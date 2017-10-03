---
title: "SAP 配接器在 SAPConnection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPConnection, supported methods, classes, and constructors
ms.assetid: a700602d-8135-4f67-a38b-770357d4e28b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b27bb8f88686fe1726aed16113ce227347151996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sapconnection-class-in-the-sap-adapter"></a>SAP 配接器在 SAPConnection 類別
下節列出方法和屬性的**SAPConnection**類別。 這代表 ADO.NET 連接到 SAP 應用程式伺服器。  
  
 這衍生自**System.Data.Common.DbConnection**。  
  
## <a name="supported-properties"></a>支援的屬性  
  
|名稱|Get/Set|Description|  
|----------|--------------|-----------------|  
|**連接字串**|取得和設定|請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。|  
|**ConnectionTimeout**|Get|不支援。 傳回 0。|  
|**資料庫**|Get|SAP 系統的識別碼。|  
|**DataSource**|Get|這會傳回 SAP 應用程式伺服器主機的名稱。|  
|**ServerVersion**|Get|這會顯示 SAP 執行個體而非 SAP 伺服器版本的版次的號碼。 例如，如果 ADO.NET 用戶端與執行個體的版次號碼 620 連接到 SAP 伺服器版本 4.6，這個屬性會顯示 620。|  
|**State**|Get|連線狀態。 支援的狀態為：<br /><br /> -[System.Data.ConnectionState]<br /><br /> 關閉<br /><br /> -開啟<br /><br /> 連線|  
  
## <a name="supported-methods"></a>支援的方法  
  
|名稱|Description|  
|----------|-----------------|  
|**ChangeDatabase(string)**|不支援。|  
|**Close （)**|關閉 SAP 系統的連接。|  
|**CreateCommand()**|傳回新的 SAPCommand 這個連接相關聯。|  
|**Getschema （)**|取得探索到的 SAP 資料表清單。 所有探索到的資料表都是在 XML 檔案 SAPDiscoveredObjects.xml。 檔案是位於\<安裝磁碟機 >: \Program Files\Common Files\Microsoft Shared\Adapters\SAP。|  
|**GetSchema(string)**|取得結構描述集合名稱為基礎。 支援集合名稱"Tables"。|  
  
|名稱|Description|  
|----------|-----------------|  
|**GetSchema （string，耗費**|取得結構描述為基礎的集合名稱和限制。 下表表示的集合名稱和支援的限制：|  
  
|名稱|集合名稱|限制|Description|  
|----------|---------------------|------------------|-----------------|  
|**GetSchema （string，耗費**|資料表|-|探索到的 SAP 資料表清單|  
|**GetSchema （string，耗費**|程序|-|探索到 Rfc 的清單|  
|**GetSchema （string，耗費**|SearchRFCs|arr [0]: 搜尋 expr|相符 Rfc 的清單|  
|**GetSchema （string，耗費**|ImportParameters|arr [1]: RFC 名稱|匯入 RFC 的參數|  
|**GetSchema （string，耗費**|ImportParameterColumn|arr [1]: RFC 名稱<br /><br /> arr [2]: name|匯入參數結構描述|  
|**GetSchema （string，耗費**|ExportParameters|arr [1]: RFC 名稱|匯出 RFC 的參數|  
|**GetSchema （string，耗費**|ExportParameterColumn|arr [1]: RFC 名稱<br /><br /> arr [2]: name|匯出參數結構描述|  
|**GetSchema （string，耗費**|TableParameters|arr [1]: RFC 名稱|資料表參數的 RFC|  
|**GetSchema （string，耗費**|TableParameterColumn|arr [1]: RFC 名稱<br /><br /> arr [2]: name|資料表參數結構描述|  
|**GetSchema （string，耗費**|ChangingParameters|arr [1]: RFC 名稱|變更參數的 RFC|  
|**GetSchema （string，耗費**|ChangingParameterColumn|arr [1]: RFC 名稱<br /><br /> arr [2]: name|變更參數結構描述|  
|**GetSchema （string，耗費**|資料行|arr [1]: 資料表名稱|SAP 資料表資料行的結構描述|  
  
|名稱|Description|  
|----------|-----------------|  
|**Open （)**|開啟 SAP 連接，根據連接字串。|  
  
> [!NOTE]
>  除了資料表、 程序和 SearchRFCs 集合項目，其他所有集合項目的您必須都指定 arr [0] 的空值。  
  
## <a name="supported-constructors"></a>支援的建構函式  
  
|名稱|Description|  
|----------|-----------------|  
|**SAPConnection()**|建立 SAPConnection 物件執行個體。|  
|**SAPConnection(string)**|接受 SAP 的連線字串。 如果連接字串無效，會擲回例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器以延伸的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)