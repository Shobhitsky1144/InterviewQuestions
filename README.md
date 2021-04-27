#Q.2 -> Iterative Python program to check Return true if the string in the first element of the list contains all of the letters of the string in the second element of the list.

def isSubSequence(str1, str2):
	m = len(str1)
	n = len(str2)

	j = 0 # Index of str1
	i = 0 # Index of str2

	# Traverse both str1 and str2
	# Compare current character of str2 with
	# first unmatched character of str1
	# If matched, then move ahead in str1

	while j < m and i < n:
		if str1[j] == str2[i]:
			j = j+1
		i = i + 1

	# If all characters of str1 matched,
	# then j is equal to m
	return j == m

# Driver Program


str1 = "gksrek"
str2 = "geeksforgeeks"

print "Yes" if isSubSequence(str1, str2) else "No"



#Q.1 -a list of customers and the number of open cash registers. Each customer is represented by an integer which indicates the amount of time needed to checkout. Assuming that customers are served in their original order, your function should output the minimum time required to serve all customers.

def checkout_time(customer_times, registers):
    time_elapsed = 0

    # each register takes the first customer in line
    registers = [customer_times.pop(0) for x in range(registers)]

    # while there is a line and all registers are not done
    while any(register > 0 for register in registers):
        # increment time
        time_elapsed += 1

        # for each register
        for x in range(0, len(registers)):
            # decrease customer times
            registers[x] -= 1

            # take the next customer in line
            if registers[x] == 0:
                if customer_times:
                    registers[x] = customer_times.pop(0)

                else:
                    registers[x] = 0

    return time_elapsed


if __name__ == "__main__":
    print(checkout_time([5, 1, 3], 1))
    print(checkout_time([10, 3, 4, 2], 2))
