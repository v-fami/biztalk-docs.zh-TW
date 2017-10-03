---
title: "疑難排解 Adapter2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wildcard characters, in send port properties
- troubleshooting adapter
- Get.xml
- send ports, using wildcards in properties
ms.assetid: e9e0408f-5a12-4f05-83a6-37dc519ae4c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991278813d2183795239d1a75c08e474b2f8159a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a>配接器疑難排解
本主題所含的資訊，可協助您辨識和解決在使用 Microsoft BizTalk Adapter for PeopleSoft Enterprise 時可能會遇到的問題。  
  
## <a name="cannot-use-wildcard-characters-in-send-port-properties"></a>無法在傳送埠屬性中使用萬用字元  
 BizTalk Adapter for PeopleSoft Enterprise 不支援在下列傳送埠屬性欄位中使用萬用字元：  
  
-   使用者名稱  
  
-   應用程式伺服器路徑  
  
-   Java_Home  
  
-   People JAR 檔案  
  
## <a name="getxml-data-assigns-0001-01-01-value-for-null-dates"></a>Get.xml 資料針對 Null 日期指派 0001-01-01 值  
 Get.xml 不正確地針對 Null 日期指派 0001-01-01 值。 如果您想要以 null 取代 0001-01-01，您必須使用 BizTalk 對應工具。  
  
## <a name="creating-and-updating-properties-with-collections-fails"></a>建立和更新含有集合的屬性失敗  
 配接器搭配 PeopleSoft 8.17.02 版使用時，配接器可以從 PeopleSoft 伺服器正確讀取資料。 不過，建立和更新含有集合的屬性將會失敗。 這是 PeopleSoft 的已知問題，可能會在 PeopleSoft 的後續版本中修正。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 peoplesoft 問題](../core/troubleshooting-peoplesoft.md)