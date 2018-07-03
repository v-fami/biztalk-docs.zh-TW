---
title: Siebel 配接器中的 SiebelConnection 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, SiebelConnection
- SiebelConnection, supported properties and methods
- SiebelConnection
ms.assetid: 661d9876-4c14-4748-b05f-cc4fd1c4ebcf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dd9e4bbf08d73c8fa48113aad1ecf12fdf0f237
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001983"
---
# <a name="siebelconnection-class-in-the-siebel-adapter"></a>Siebel 配接器中的 SiebelConnection 類別
[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]存取基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] `Binding`，則`ConnectionFactory`，和`Channel`連接至 Siebel 系統。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]實作`DbConnection`類別，以支援上述功能。  

 使用的執行個體`Microsoft.Data.SiebelClient.SiebelClientFactory`，用戶端程式可以取得的執行個體`System.Data.Common.DbConnection`類別來連接至 Siebel 系統。  

```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  

 或者，可以用下列方法，來建立連線：  

```  

SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  

 `SiebelConnection`類別繼承自`DbConnection`。 命名空間中存在`Microsoft.Data.SiebelClient`。  

## <a name="supported-properties"></a>支援的屬性  
 `SiebelConnection`類別支援下列`DbConnection`屬性。  


|         [屬性]         |   取得或設定   |                                                                                                      描述                                                                                                       |
|----------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ConnectionString** | 取得和設定 |                                                                                  取得或設定用來開啟連接的字串。                                                                                  |
|     **[資料庫備份]**     |     Get     |        取得後開啟連接時，目前資料庫的名稱或連接開啟之前，連接字串中指定的資料庫名稱。 這應該是 Siebel 儲存機制名稱。         |
|    **DataSource**    |     Get     |                                                                                取得此連線的 Siebel 閘道的名稱。                                                                                |
|  **ServerVersion**   |     Get     | 在目前版本中的[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，這個屬性會傳回硬式編碼值，不代表實際的 Siebel 伺服器版本。 |
|      **State**       |     Get     |                                               取得描述連接狀態的字串。 這個檔案可以包含三個可能的值： 開啟、 中斷或已關閉。                                               |

## <a name="supported-methods"></a>支援的方法  
 `SiebelConnection`類別支援下列`DbConnection`方法。  

|[屬性]|描述|  
|----------|-----------------|  
|**CreateDbCommand**|此受保護的方法提供新的 DbCommand 例項。|  
|**ChangeDatabase**|這個公用方法不支援，而且將會擲回例外狀況，如果呼叫。|  
|**開啟**|開啟與 Siebel 系統的連線，藉由建立 WCF 通道。|  
|**關閉**|關閉 WCF 通道會關閉與 Siebel 系統的連線。|  
|**CreateCommand**|建立命令物件。|  

## <a name="see-also"></a>另請參閱  
 [使用 Siebel 配接器擴充 ADO.NET 介面](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)