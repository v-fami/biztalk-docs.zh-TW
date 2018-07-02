---
title: 中繼資料錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07167c2c0189c36f7b1a321d81bd0070398953e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975119"
---
# <a name="metadata-errors"></a>中繼資料錯誤
診斷及解決 WCF 中繼資料錯誤的資訊。  
  
## <a name="error-consuming-wcf-service-metadata"></a>取用 WCF 服務中繼資料時發生錯誤

|                 |                                   錯誤詳細資料                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                        取用 WCF 服務中繼資料時發生錯誤                        |
  
### <a name="explanation"></a>說明  
 此錯誤表示中繼資料可供服務可能未提供或無效。  
  
### <a name="user-action"></a>使用者動作  
 更正的服務中繼資料，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務時）。 移至 服務組態編輯器 (**svcConfigEditor.exe**) 並對組態檔進行變更。  否則，請連絡服務提供者

## <a name="failed-to-get-metadata"></a>無法取得中繼資料

|                 |                                   錯誤詳細資料                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                          無法取得中繼資料 」{0}                          |
  
## <a name="explanation"></a>說明  
 此錯誤表示中繼資料不是適用於該服務。  
  
## <a name="user-action"></a>使用者動作  
 啟用服務中繼資料並執行使用精靈一次 （如果您擁有想要使用的 WCF 服務時）。 否則，請連絡服務提供者。