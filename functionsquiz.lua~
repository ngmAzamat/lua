local json = require("dkjson")

function GetQuestionList(json_file_name)
	local file = io.open(json_file_name, "r")
	local data = file:read("*all")
	file:close()

	local jsonData, pos, err = json.decode(data, 1, nil)
	
	if err then
		print("Error:", err)
		return nil
	end
	
	return jsonData
end


function green(message)
	print("\27[32m")
	print(message)
	print("\27[0m")
end

function red(message)
	print("\27[31m")
	print(message)
	print("\27[0m")
end


function question(question, options, answer)
	green("\nQuestion : " .. question .. "\n")
	
	for key, value in pairs(options) do
		print("\t" .. key .. ") " .. value)
	end

	local choice = io.read("*n")
	-- print(type(choice))
	-- print(type(answer))

	if choice == answer then
		green("OK")
		return true
	else
		red("ERR")
		return false
	end

end

function RunQuiz(json_file_name)
	local counter = 0
		
	local questionlist = GetQuestionList(json_file_name)
	
	for key, value in pairs(questionlist) do
		 result = question(value.question, value.options, value.answer)
		if result then
			counter = counter + 1
		end
	end


	local number_of_question = #questionlist
	local result = counter / number_of_question * 100 
	
	return result
end





